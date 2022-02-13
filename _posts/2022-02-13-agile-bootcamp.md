---
title: 敏捷培訓心得
author:
  name: Pan Yueh-Sheng
  link: https://github.com/pauleezz
date: 2022-02-13 21:00:00 +0800
categories: [Internship, CAP]
tags: [Agile Bootcamp, Scrum ]
math: true
mermaid: true
image:
  src: /posts/20220213/methodology-agile.png
  width: 800
  height: 500
---

這篇筆記主要是記錄在參加國泰CAP實習舉辦的敏捷培訓時所學習到的知識，並且再加上寒假這段時間在實習時每日參加的CCMA Daily Sync所得出的心得。之前大學二年級的時候第一次聽到這個名詞，上網查了之後也沒有很了解到底是在敏捷什麼，也沒有再繼續深入研究。這次的培訓是由柯仁傑老師來介紹敏捷開發的特色以及應用。


## 敏捷觀念簡介
每次講到敏捷軟體開發時，少不了的就是敏捷宣言（Agile Manifesto）了，當初考研究所補習時資管課本也出現過，當年台大資管所題目也有考出來，其宣言如下:
* <span style="color:blue">個人與互動</span> **重於** 流程與工具 
* <span style="color:blue">可用的軟體</span> **重於** 詳盡的文件 
* <span style="color:blue">與客戶合作</span> **重於** 合約協商 
* <span style="color:blue">回應變化</span> **重於** 遵循計劃 

### <span style="color:blue">個人與互動</span> **重於** 流程與工具 
在專案近行時，流程與工具只是達成的手段，最重要的其實是與你一起進行開發的團隊夥伴，若是大家有很好的溝通、討論方式，可以讓專案成功的機率大大增加。
### <span style="color:blue">可用的軟體</span> **重於** 詳盡的文件 
在宣言裡面，開發過程中並沒有進度條（e.g. 已完成80%）的情況，只有可不可以運作的產品，這樣的想法是因為專案產出的目的是要提供給使用者使用，假設沒有完成，其實意義就不大了。
### <span style="color:blue">與客戶合作</span> **重於** 合約協商 
消費者的需求可能隨著時間產生改變，若只依照合約所明示的項目進行開發的話，很難及時應對將來潛在的變化，且需要再花時間討論合約的修改，導致效率低下。
### <span style="color:blue">回應變化</span> **重於** 遵循計劃 
在專案一開始時，整個輪廓並沒有這麼的明確，因此會需要多次與使用者進行溝通並提出改善，若是埋頭一直自己做事可能會使產品做出來時與客戶期望不同，增加更多的溝通成本。

在這邊常常出現一個誤解，認為例如說只要可以交出軟體就好不需要再去寫詳細文件。事實上，兩邊都是非常重要的，只不過左邊的重要性在略高於右邊，但並不代表右邊的部分就不重要，就完全地捨棄它。


![](/posts/20220213/agile_umbrella.png)

從這張圖可以發現，除了常聽過的Scrum, Kanban, XP等方法外，還有其他不同的開發方法包含在Agile的雨傘底下。其實只要符合Agile宣言精神的都可以叫做Agile的方法，而其中Scrum是裡面最流行的一種方法，原因是他相對其他的方法好學習，角色分工明確，又不會提到太多的技術細節，老闆也會聽得懂內容，但也是最難精通的方法。

## Scrum 基礎觀念介紹

![](/posts/20220213/sprint_framework.png)
上圖是Scrum的框架，接下來會列出我覺得一些比較特別的地方：

### Product Owner (PO)
將要做的事情和需求列出來、排出優先順序並放在Product Backlog中。

### Scrum Master (SM)
看團隊有沒有依照Scrum的流程來執行。

### Product Backlog
產品需求項目清單（Product Backlog Item）種類主要分為四種，分別是需求、錯誤、技術債、技術評估。列出的需求可能透過使用案例、使用者故事或是任何其他格式來做表達，錯誤是之前在開發過程中出現的Bug，技術債是之前可能為了能夠快速開發在應該採用最佳方案時進行了妥協，改用短期內能加速軟體開發的方案，使得在未來可能帶來的額外開發負擔，最後的技術評估則是因為不知道這個項目要怎麼做，所以要花時間來評估怎麼做。

**Product Backlog Item的排序依據是尤其商業價值來去做排序**

可以發現Product Backlog前面的項目比較細，然後越後面的項目越大，會這樣顯示的原因是Product Backlog較前面的代表優先順序越高，是最近就要完成的事情，因此要做的事情也會釐清的比較清楚，並且切分的會比較細。

### Sprint Planning
在Sprint的第一天開始Sprint規劃會議，根據開發團隊的開發速度，從Product Backlog中選擇這次要做的Item有哪些，並且放入Sprint Backlog中。


### Sprint
一個Sprint可能會歷時1-4週，最常見的是兩週一次。在Sprint開始時會有一個Sprint Planning，從Product Backlog中決定這個迭代要做哪些事情，並放到Sprint Backlog中。

### Daily Scrum
開發團隊與Scrum Master每天早上會開一個15分鐘的的會議（產品負責人與利害關係人可選），主要目標是要互相了解大家的進度如何，討論主題主要包含「昨天完成了什麼」、「今天打算做甚麼」、「遭遇到了什麼阻礙與困難」這三類。「遭遇到了什麼阻礙與困難」重要之處是因為在提出自己遇到的問題時，自己遇到的問題可能是別人也會遇到的問題，達到互相交流的效果，同時也可以讓大家更Involve在會議之中。要注意的是，在這其中只會提出問題，不會當下討論細節、怎麼解決，這樣才能確保Daily Standup能在15分鐘內完成。

Daily Standup 也可以判斷出一個團隊的氣氛如何，從一開始有沒有人願意開始分享或者是提出問題時有沒有人願意主動提出幫忙，可說是團隊氣氛的照妖鏡。

### Sprint Review
在完成一個Sprint後舉行，由整個敏捷團隊（開發團隊, SM, PO）與利害關係人共同<span style="color:blue">檢視及驗收</span>這次Sprint所完成的事項，將做完的項目（可用的軟體才算產出）放在Increment中，未完成的項目再放回到Product Backlog中，重新排優先順序。
在Sprint Review最重要的目的是要給stackholder展示目前的進度及結果為何，在展示的過程中，要注意做完就先demo，才能及時調整，才不會發現沒有通過標準卻沒有時間進行修改、以講故事的型態來展示，且展示時間不要太長、展示對象也要確定找到對的利害關係人、對於任何的回饋要保持開放。

### Sprint Retrospective
在一個Sprint結束前、檢視會議結束後會開Sprint Retrospective，來去看在這次執行過程中發生了甚麼問題、如何改進等等，希望做事方法能夠更有效率，讓下一個Sprint能夠運行得更順利。

#### Sprint Retrospective流程圖
![](/posts/20220213/retrospective.png)

一開始討論時可能會不知道要從哪個部分開始討論，這時候可以先設定一個方向先討論，再去深討發生的原因並作出改善。此外雖然一個問題在被討論之後可能不會完全被解決，但是可以降低這些問題發生的可能性。

#### 4個常見的Sprint Retrospective的做法

* **Start, Stop, Continue**
* **Mad Sad Glad**
* **Speed Boat**
* **魚骨圖**

### Start, Stop, Continue
![](/posts/20220213/start_stop_continue.png)

### Mad Sad Glad
![](/posts/20220213/mad_sad_glad.jpeg)
幫助團隊去尋找哪些讓他們開心、難過、生氣，甚麼事做得好，甚麼事可以再做改進，讓大家互相瞭解對方的想法，並從中改善、增加團隊士氣及工作滿意度

### Speed Boat
![](/posts/20220213/speed_boat.png)
目的：讓團隊清楚知道每個項目的意義，以及釐清為什麼是放在這個分類

* Goal: 要達成的目標
* Helping team: 幫助專案順利進行的原因
* Delay: 延後目前專案進度的原因
* risk: 可能導致**將來做得比較慢的原因**


### 魚骨圖
![](/posts/20220213/fish_bone.png)

這些Sprint Retrospective其實目的都差不多，只是用不同方式來進行。

**Scrum只有說要做甚麼事情，沒有告訴你怎麼做，因此每個團隊可能都有不同的做法**

---

敏捷宣言的起草人Jeff Sutherland說過，在執行Scrum時要考慮的問題有兩個: 

#### <span style="color:blue">經常檢查你的方向是否正確，你  做的東西是否是客戶要的？</span>
隨時跟客戶保持溝通一致，假如做的是不是user要的，才能及時做更改
#### <span style="color:blue">是否有更任何方法，可以改進目前作法，讓你更快更好？</span>




## 用戶故事/用戶故事地圖

老師提出了「建立高鐵售票網站」的題目，讓小組在短暫的時間內去發想可能的功能有哪些？並使用使用者故事（User Story）的方式來表達，格式為以下：
### As a [role] I can [function] so that [business value]
e.g. As a bookstore customer, I can search for book by the title, So that I can easily find all books with that title.

在這裡的business value所要表達的是為什麼要這個功能?要解決的是甚麼事？並且是使用商業語言來去描述。藉由User Story我們就先拿這個東西讓我們可以跟用戶<span style="color:blue">討論</span>再來擬定細節，並不是就不寫細節，這邊的重點會是在<span style="color:blue">討論</span>這塊。

討論過程中，常常是想到什麼就填上什麼，並沒有一個系統性的方式，導致後面較難想到新的功能。這時候，**User Story Mapping**就會是非常重要的角色了。如果單純從頭發想User Story，想出來的項目常常沒有統整性，只是想到甚麼就甚麼，這時候透過使用者流程來模擬各種使用上可能會用到的功能，就可以更有系統性的條列出來。

一個User Story Mapping包含了User Goal，並以Persona來描述使用者輪廓，這樣老闆才會了解這樣做的原因為何。

以下是User Story Mapping範例：
![](/posts/20220213/user_story_map.png)

橫軸是工作流程順序，縱軸是優先順序，裡面的便條紙可能是一個功能或是故事。可以發現除了不同的Epic, Story外，也有分成三個Release順序，第一個release主要會是以最簡單的功能出發。

最後的高鐵線上購票系統就會長這樣：
![](/posts/20220213/THSR.png)
包含了訂票、付款、取票、退票、效能等high level的需求描述，並先從網頁開始開發，再進階到7-11、手機整合到最後的優惠組合。

## Scrum...要考慮的點



### 評估原則
要如何有效地評估出這次Sprint可完成的項目數呢？主要分為兩種做法：
1. 憑感覺
2. 計算速度

比較常用的方式是透過感覺的方式，利用之前的經驗來做判斷，或根據這幾周平均完成幾件事來去做判斷。

在評估項目數的時候，有一些方法可以遵循...
* 小比大容易
以拼樂高為例，假如是拼出一個小玩具或零件的話，可以容易地獄沽出可能要花多久時間完成，那麼假如要拼一個很大的樂高的話，每個人預估要花的時間就會相差很大，或是準確度很低。因此將一個很大的項目拆分乘小項目來去記算時，時間估算會比較精準。
* 相對比絕對容易
以101為例，直接判斷出101準確的高度是有難度的，那麼假如換成是以微風南山為基準，101的高度是它的幾倍呢？這時候就可以透過比較的方式來有效地估算出來。在敏捷開發也是一樣，找一個story為基礎，去判斷出其他story難度的相對差距為何，來決定他大概需要花多少時間來完成。而評估story難度的方式常選擇一個項目作為基準，並設定Story Point成5分來跟其他項目做比較。

### 故事點數（Story Point）
可以用來表示該項目複雜程度，可以用在User Story, 功能, 某個工作上，並從<span style="color:blue">開發的複雜程度</span>以及<span style="color:blue">開發的風險</span>來去界定。Playing Poker是一個常用在團隊中決定Story Point多寡的一種方法，進行方式是每個人來投票這項story的點數為何，假設結果差距很大時，再請投出高分與低分的同仁來分享給分數的想法，之後再進行第二輪投票。

Story Point的目的不是要去精確的估出分數為何，而是要讓大家的想法清楚表達，確保透明度假如估出來的分數很大，那麼可以再細分該項目，讓各個細項的預估能夠更準確。

### 做完的定義是什麼？
如何定義做完一個項目？做完代表的是<span style="color:blue">可以提交給用戶使用</span>，對於Sprint來說，做完代表的是已經展示過了、並已經更新Product Backlog，對於故事來說，做完代表的是單元測試、功能性測試完成、沒有P1/P2的bug，確定好做完的定義有哪些後，才能讓大家了解何謂做完，也更能預估出完成所需要的時間。

在驗收條件方面，可以是由一堆敘述所組成，並清楚定義出通過和失敗的標準為何，也就更容易地判斷出這項目是否滿足驗收條件，且對每一條功能列出驗收標準，將來的結果也更能<span style="color:blue">符合客戶的期望</span>。

範例：
**User Story**:
作為**用戶**，我希望能夠**註冊服務**，以便我可以**開始線上購物**
**驗收標準**:
1. 用戶必須填完所有必填欄位才能提交註冊
2. 來自同一個IP地提交，只能在30分鐘內提交3次
3. 用戶註冊成功後會收到通知郵件


> 事實上，一個Story做完比Task做完重要很多

## Scrum 開發方法總結
Scrum有明確的角色分工、進行流程，使得這個框架讓人容易學習，但是就像圍棋比賽一樣，瞭解規則是不夠的（只看教學影片就變強），需要實際動手做、有教練指導才能真正進步。

## 參考資料

* 上課內容
* [What is Agile? What is Scrum?](https://www.visual-paradigm.com/scrum/what-is-agile-and-scrum/)
* [What Is Agile Methodology In Project Management?](https://hive.com/blog/what-is-agile-project-management-methodology/)
