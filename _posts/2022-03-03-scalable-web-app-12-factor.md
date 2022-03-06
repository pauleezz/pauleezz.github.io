---
title: 可擴展Web應用系統的十二項架構設計原則
author:
  name: Pan Yueh-Sheng
  link: https://github.com/pauleezz
date: 2022-03-03 21:00:00 +0800
categories: [Development]
tags: [Memo]
math: true
mermaid: true
# image:
#   src: /posts/20220303/methodology-agile.png
#   width: 800
#   height: 500
---

此篇文章主要是記錄2022年3月3日由Philipz鄭淳尹分享：[可擴展Web應用系統的十二項架構設計原則](https://www.youtube.com/watch?v=9vs_DQRAip4)的內容，並把自己覺得重要以及不會的知識記錄下來，未來有需要回故時能夠快速查找。

## The AKF Scale Cube
![](/posts/20220303/akf_cube.png)

**Scale Cube** 是由一個科技顧問公司AKF所提出的一個系統設計模型，其中定義了怎麼切分服務、如何scaling產品等等。模型總共分為三個維度（X, Y, Z軸），其分別代表的是：
* X軸：水平擴展，將服務和資料複製多份，如K8S的水平擴展
* Y軸：根據功能、業務或相似的內容來對系統進行拆分
* Z軸：根據服務或是資料進行Sharding分區，如建立兩個Data Center在不同Region

## 十二原則

### 原則一：避免過度設計

不一定每個都需要用到微服務架構或複雜的解決方案，因為實踐成本過高、維運麻煩，越難找到問題。例如綠界科技系統原本拆分成微服務架構並透過API呼叫，但是因為response time太慢，最後的解決方案是把各個服務集中到VM上，使得API呼叫時，減少網路延遲的狀況。此外在Istio設計文檔也提到：「過早的優化複雜性是萬惡之源，或者：我如何學會停止擔心並熱愛單體應用」。
對於是否已經過度設計可透過測試同仁是否可以輕易理解架構設計方案，來驗證是否過度設計。

-> 業務的量還沒到不需要過早優化

### 原則二：服務X軸擴展

當應用伺服器的CPU或Memory使用量高時，複製相同服務（透過VM或容器）來分攤運算負載。假設應用系統沒有被設計成Stateless或是資料外部化時（cache, storage, DB），必須把Load Balancer設計成sticky sessions，確保使用者在sticky時間內都會連線到同一台伺服器，或是使用集中式的session儲存伺服器（e.g. Redis, Hazelcast, Ignite等），確保其他伺服器也可以有狀態資訊。其他共用檔案可透過NFS掛載或是寫到資料庫來達到Stateless。

-> 無需改寫程式，但無法根本解決問題、維運成本增加

### 原則三：資料X軸擴展
當資料庫讀寫比例、CPU用量高時，可透過複製相同資料庫來分攤交易時的讀寫。將單一資料庫拆分成唯獨及唯寫的讀寫分離架構（CQRS），寫入（20%）時寫到Master Node，讀取（80%）時使用Slave Node。建議透過標準的API或channel來access DB，而不是直接去使用。例如MySQL解決Scaling（沒有InnoDB）的方式是把read command透過Virtual IP到replica讀取，而write command則是直接寫入到source中。

<img src="/posts/20220303/mysql.png" alt="" width="200"/>

> X軸擴展優劣分析
> pros: 易於實現，最常使用
> cons: 需要完整複製資料，增加成本、session共用會導致可用性及可擴展性問題

### 原則四：服務Y軸擴展

根據不同業務、Domain來拆分資料、系統、開發團隊，解決大型複雜系統在開發時團隊耗費大量時間在溝通以及系統功能耦合。可參考資料的ER Model或Domain Driven Design設計方法來拆分服務、利用APM監控系統瓶頸，將回應時間長的服務獨立出新服務或依照Database per service設計模式避免拆分出的服務存取到其他服務的資料，當資料異動時影響其他服務

### 原則五：資料Y軸擴展
將資料庫分成不同功能（線上交易作業與BI報表作業分開、Report job從唯獨副本執行分析），達到資料分流

> Y軸擴展優劣分析
> pros: 增加可擴展性（根本解決）
> cons: 重構系統複雜度增加，更多服務複雜度指數增加，成本高

### 原則六：服務Z軸擴展
面對全球性服務，地理位置網路物理距離成為系統效能瓶頸，因此需要根據使用者獨特屬性來進行服務分流。解決方法有：
1. 基於HTTP，使用Global HTTP Load Balancer達到Content-Based Routing
2. 基於DNS，使用支援動態DNS的LB服務，在客戶查詢DNS解析時，根據客戶IP回傳最近的服務
3. 前端靜態網頁的JS配合後端Content-Based Routing分流

-> 避免單一區域failure影響整體服務，可透過IaC加速建置及降低為運成本

### 原則七：資料Z軸擴展
若單一資料表比數非常大，造成資料庫執行效率過低，且短期無法優化或修改程式拆分為多個資料表時，可利用Sharding或垂直分片、水平分片來增加效率，一般較常用水平分片，除非業務邏輯改變，否則避免採用垂直分片

分片策略
* Key-Based: 選定其中一列為shard key，並透過hash function分配
* Range-Based: 價格0~49, 50~99的分開
* Dictionary-Based: 按照客戶所在地區區分
* Entity Groups: 相關的表格放在同一分片中，有更強的一致性

-> 減少indexing時間，Data Center異地多活（AA mode），GCP Cloud Spanner可同時改善資料庫和跨區域資料一致性問題

#### 案例：Vitess - 自動化分片中間層
背景：YouTube業務增長（2010），單一資料庫無法容納資料，勢必須要進行分片
解決方法：
1. 讀寫分離：為寫入流量建立一個主要資料庫，讀取流量另建一個副本資料庫
2. 讀取流量仍造成副本資料庫超載，因此增加更多副本資料庫，作為臨時解決方案
3. 寫入流量過高，對資料進行分片
4. YouTube application layer經過修改，讓程式可以識別正確的資料庫分片進行查詢

Vitess在應用層與資料庫間引入**代理**來routing和manage資料庫，透過中間層代理來具備橫向擴展能力

![](/posts/20220303/vitess.png)

MySQL: 每個MySQL主備叢集由一個MySQL主服務器和一個或多個MySQL從服務器組成
VTGate: 作為單一入口並導流到不同MySQL主備叢集，導流/分片邏輯放在Topology裡，知道存放位置後進行SQL拆分，將子SQL分發給各個VTTablet裡，VTTablet回傳結果後再聚和、排序回傳到client
Topology: 維護Vitess叢集的metadata，e.g. 某個資料庫的各個分片都儲存在哪些MySQL主備叢集上

> Z軸擴展優劣分析
> pros: 因地制宜，例如分割機房pod，以便符合當地個資法
> cons: 無法根本解決組織上問題，主要是進行分流

**X軸、Y軸可以解決系統performance的問題，但無法解決開發上performance的問題**

### 原則八：善用公有雲服務

當業務需求有臨時性、突增性需求，或開發新型態業務面對未來需求的不確定性便可使用公有雲服務降低建制機房成本

### 原則九：選擇適當資料庫
綜合考量數據量、儲存量、回應時間等因素選擇適合的工具。例如關連式資料庫適合：交易的一致性、ACID屬性，但成本高難以擴展。

* OLTP: Row oriented
* OLAPL Column oriented

![](/posts/20220303/sql_nosql_compare.jpeg)

ClickHouse: 可以進行SQL查詢的OLAP

### 原則十：務必使用分散式監控系統

服務X軸擴展及Y軸擴展後，大量應用系統在監控時會造成維運負擔，且出現問題時難以查找。使用可觀測性（Observability）的分散式解決分案來診斷及預防系統問題，可觀測性方案分為：
* logging日誌
* metrics指標
* tracing追蹤
將這三大資料集中儲存及分析，以便確認問題，或根據監控數據規劃運算資源。

![](/posts/20220303/obserbility.png)

[OpenAPM](https://openapm.io/landscape)這個網站可以查詢各個平台服務可以紀錄、查詢哪些資料，並做出互相搭配，確保可以組合運作。

### 原則十一：設計分層快取機制

減輕核心系統負擔，減少到資料庫的網頁請求量，節省網路頻寬。可透過

1. 把前端靜態網頁檔案放置到CDN服務
2. 開放網路設備快取機制，減少後端讀取次數
3. 使用Web, Reverse proxy, API Gateway快取機制
4. 設計應用伺服器的集中式快取架構，如：Redis, Hazelcast, Ignite等
5. 大量且重複的資料庫查詢可使用Object/Entity快取功能，如JPA cache或Hibernate cache等
6. 使用資料庫本身的快取如：memory table, IMDG等，但可能被廠商綁定

![](/posts/20220303/cache.png)

### 原則十二：適時採用非同步通訊方式

無法透過增加硬體設備來改善系統效能時，可修改既有架構設計或改成非阻塞式的響應式程式設計，透過Message Broker（IBM MQ, Kafka）設計非同步是通訊，或使用響應式（Reactive）開發框架拆解服務溝通方式（成本高）。
從業務流程分析或事件風暴（Event Storming）了解現有流程是否可以使用非同步方式取代，例如星巴克的二階段交付，先結帳再叫名取餐。將訊息（Message）分成須確認結果的命令（Command）和單純傳遞已發生的事件（Event），Command使用支援Request-Reply的MQ，事件則使用Fire&Forget的可擴展Event Bus，如Kafka

Enterprise Integration Patterns書中主要是在討論大企業系統如何進行整合、溝通，這本書的作者寫了篇文章：Your Coffee Shop Doesn't Use Two-Phase Commit，裡面提到應用程式要跟partner API溝通，但是外部相依性服務溝通成為瓶頸時，可使用非同步的方式：首先Client使用結帳API，結帳API先被寫入到Queue中，接著Queue的API的應用程式再慢慢的消化Queue，完成後再透過topic訂閱的對外專用API來做通知，呼叫partner信用卡API，partner信用卡API回傳結果後寫入資料庫，這時Client就可以使用結帳API來查詢交易結果。

![](/posts/20220303/async.png)

### 大型企業應用系統架構

![](/posts/20220303/enterprise_app_structure.png)

## Reference

[十二項架構設計原則簡報](https://www.slideshare.net/philipzh/ss-251273250?fbclid=IwAR15sKppSxu0vYgtuMNbX3-awwzJQtO22XnTwtGTUPJeUthc0P6HHKJvyBw)
[THE SCALE CUBE](https://akfpartners.com/growth-blog/scale-cube)
[SQL vs. NoSQL Database: When to Use, How to Choose](https://towardsdatascience.com/datastore-choices-sql-vs-nosql-database-ebec24d56106)