---
title: PDIS-RAY4.0 實習心得
author:
  name: Pan Yueh-Sheng
  link: https://github.com/pauleezz
date: 2019-09-06 11:33:00 +0800
categories: [Internship, PDIS-Ray4.0]
tags: [Design Thinking, Ui Ux Design, Web Development, Website Design ]
math: true
mermaid: true
image:
  src: /posts/20200906/groupphoto.jpeg
  width: 800
  height: 500
---

2020年的暑假，我參加了[RAY 4.0青年學生體檢政府網站計畫](https://ray2020.pdis.nat.gov.tw/)的見習生。初次耳聞這個計畫是從同學討論『欸這計畫可以看到唐鳳耶！』之中得知，在看了計畫說明後發現對於這個計畫十分有興趣，報名後也很榮幸地被錄取了。這兩個月的累積讓我學到事情。所以想藉由剛結束記憶猶新時，分享這段時間的一些心得，也讓大家參考參考。

## PDIS&RAY4.0是什麼？

[PDIS](https://pdis.nat.gov.tw/zh-TW/) (Public Digital Innovation Space)中文名為公共數位創新空間，主要是協助政府部會提升數位服務品質，以服務設計思維優化公務體系的流程和工具。

RAY4.0，全名為Rescue Action by Youth .gov 2020，也就是這個青年學生體檢政府網站數位服務專案本身，招募30位青年學生一同優化政府網站數位服務，並進行檢核、設計出改善後的原型。在專案中不時有部會工作坊和定期見面會，一同與機關同仁協作和分享進度與其他小組互相交流。

## 見習內容

我們這組負責的是[基隆市政府全球資訊網](https://www.klcg.gov.tw/)(目前網站頁面已更新設計) 的網站服務改善，整個專案大致分為四大流程：

### 一、暸解 User
這個階段主要分為兩個部分：
#### 網站現況分析
我們實際操作網站，並嘗試列出網站的主要服務，但卻發現很難清楚界定各項服務內容以及各服務的取得路徑，因為基隆市政府主要是以機關導向提供查詢，假設不清楚所需的服務是隸屬於哪一機關，便無法取得所需的服務。我們也檢視了網站的整體布局及分析網站資訊架構，發現目前基隆市政府的資訊架構是混亂且不易釋讀的。

與部會人員訪談中，得知基隆市政府全球資訊網是屬於整合資訊式的網站，他們也希望透過整合各項的服務分類，以服務歸納的方式來簡化資訊取得複雜度。
#### 使用者研究
針對上述的網站現況分析所確立出的目標與問題，我們廣發使用者問卷並招募了受訪者進行使用者研究，訪談主要分為三個步驟進行：使用者訪談、網站易用性測試、使用者分類服務。藉由使用者訪談所得到的資訊，我們透過親合圖法找出使用者痛點及需求，並透過網站易用性測試中所設立的任務，來挖掘他們在找尋過程中遇到的痛點以及想法，最後的使用者分類服務則是透過讓受訪者列出主要功能與網頁架構排序的分類方式，來了解對於使用者來說較為重視整府網站的服務類型及功能佈局的呈現方式為何。

![Interview Feedback](/posts/20200906/feedback.png)
_使用者訪談中所得到的回饋_
### 二、定義核心議題
針對上個階段的結果，我們擬定了Persona和Customer Journey Map以確立使用者輪廓和釐清操作過程中的旅程以及斷點，並定義出了關鍵問題共有：服務歸納不清楚、服務命名不直觀、網站內容頁面說明不足和基隆在地特色未充分展現四個面向，並根據各關鍵問題提出改善方向，成為後續進行網頁改善的參考依據。

![Improve](/posts/20200906/improve.png)
_根據關鍵問題所提出的四大改善方向_

為了重新歸納服務，我們決定從訂定資訊架構開始，藉由盤點各個服務，將相似的服務整合並群組成一個類別。因為基隆市政府網站屬於統整性的入口式網站，因此在分類方向上，主要是透過廣而淺而非窄而深的方式，透過廣做為入口，讓使用者從眾多服務中，快速找到對應的網站及資訊，不需要層層地費時尋找所欲查詢的目標。而在各類別命名方面，目標是能讓名稱能妥善代表該類別的內容，同時強調彼此類別的區別性，減少混淆的發生。在導覽列頁面，我們發現便民服務、市政服務、主題服務館三個區塊中，部分的服務內容重疊，且僅列有少數服務，因此我們決定整併這三區的服務內容，形成主題服務，並增設市政資訊作為政府提供資訊的窗口。
### 三、打造 Wireframe
在這個階段的目的主要就是打造初步網站的架構雛形，我們設計了A版、B版兩種版本，分別代表著基本、可行性高和有創意、突破框架兩個版本，探索更多設計可能，最終融合兩種wireframe測試結果。

在A版本方面，因為基隆市政府已經開始著手進行網頁改版計畫，所以我們以即將改版的網頁layout為參考，並從先前與部會人員所討論出的結果，依照機關與民眾需求更動服務項目的優先順序。為了將各服務妥善歸類，我們一一將各服務逐層分類，最終歸納、命名出了12大類別項目，各類別在瀏覽時也會跳出該類別的重點服務，讓使用者能夠快速了解各類別含義。點入類別後，各項服務會提供簡短說明、網站名稱，讓試用者能快速了解該服務內容。

![A版本12大類別項目](/posts/20200906/wireframe_a.png)
_A版本12大類別項目_

B版本方面，在參考各國政府網站時，我們發現像夏威夷、密西根、香港等網站都有以身份別的分類來幫助取得各個服務，這也成為我們打造B版wireframe的靈感來源，將網站大致分為三種身份別：觀光旅客、政府服務和基隆市民，重新分配各服務項目的所在位置。

![B版本分眾服務](/posts/20200906/wireframe_b.png)
_B版本分眾服務_

### 四、Prototype設計
經過使用者訪談、測試後，我們發現兩種版本的wireframe皆有各自的支持者，最終決定將兩種服務呈現方式同時納入prototype裡，並命名為基隆服務，迎合不同搜尋模式偏好的使用者，並根據使用者回饋，將B版本的政府服務改名為非基隆市民，減少名稱誤解的發生。


![兩個不同版本的服務分類方式](/posts/20200906/prototype_a.png)
_兩個不同版本的服務分類方式_
在招標資訊和徵才資訊上，我們根據使用者所提供的建議，於標題前方加上標籤提供使用者快速搜尋，並將頁面分為簡版與詳版的設計以提供不同資訊量與內容呈現，讓不同目的（只是大致瀏覽資訊或逐一仔細閱讀）的使用者都能方便的使用。


![詳版與簡版的資訊呈現](/posts/20200906/prototype_b.png)
_詳版與簡版的資訊呈現_
使用XD設計頁面同時，我也開始了網站建置的工作，網站以React為框架，Bootstrap協助版面配置。[程式碼連結在此](https://github.com/pauleezz/Keelung-Website)

![XD上滿滿的頁面](/posts/20200906/prototype_c.png)
_XD上滿滿的頁面_
同一時間Protype也在使用者訪談中所得到的回饋下，經過Low-fidelity 到high-fidelity的層層迭代與修正，形成了最後網站的樣貌。

![high-fidelity prototype首頁頁面](/posts/20200906/prototype_d.png)
_high-fidelity prototype首頁頁面_
## 見習心得
在此之前比較少有參與設計相關的經驗，這次也著實讓我學到許多UI/UX的知識。與組員交流、進行設計思考中也讓我瞭解到，設計出一個方便、人性化的網站是多麽的困難，需要考慮的因素眾多，不論是在使用者訪談、定義關鍵問題、wireframe的建立等階段都是需要嚴謹的分析和討論才能完成。

因為專案主要是以遠端進行，雖然時間調配上變得充裕，但是與組員協作時的時間掌控就變得十分重要。如何擬定時間、因應迭代做出時間配置的更動，將任務繼續傳遞下去讓我獲益良多。

在每個小組中，有Designer, Researcher和Engineer三個角色，身為Engineer的我在這次專案中比較屬於輔助的角色，目的是在設計網頁時提供實際建置時可能會發生的難處以及需要考慮問題。因為是組內唯一的工程師，因此網站的建置主要是由我所完成。要在短短一個多禮拜的時間完成多達時間完成40個網頁的程式碼也是全新的挑戰，這個過程中也讓我了解到系統規劃的重要性，將可重複利用的元件模組化、模擬可能的使用情境減少錯誤狀況發生，這些應用讓我可以在減少開發時間下，仍然能夠完善完成網頁建置。

在部會工作坊中，與部會人員分別討論到了公部門在執行決策時所要考慮的限制，以及此更動影響到哪些項目、利害關係人，讓我對公部門的執行有更加了解。而每次的見面會也都讓我受益良多，不僅可以了解到其他組別的進行方式以及個別的創新做法並加以學習，報告後的提問時間也可以藉由其他組的所提出的疑問來找出組內沒有看出的問題、盲點，並且反思目前所做的部分如何改進、讓研究更加完整。

![部會工作坊合照](/posts/20200906/workshop.jpeg)
_部會工作坊合照_
這次讓我學習到最多的就是團體合作方式了，像是任務分配、組員協作及溝通，也讓我深深了解到團體的重要性。因為一次徵求受訪者的失誤使得遭到投訴，在第一時間內組內不是互相指責找出代罪羔羊，而是檢討在整個約訪流程中所發生的疏失以及如何改善，並致電道歉，在下次的見面會也與其他組分享這次的經驗提供警惕。這次的經驗讓我瞭解到良好的團隊再發生問題時是一起解決問題，做出最好的災害應變而不是互相推卸。

這短短的兩個月咻的一下就過去了，回想報到當天好像只是不久前的事情，不論是在定期見面會享用超級好吃的美食、前往基隆進行訪談結束後拖著疲憊的身軀回家、部會工作坊和討論時進行腦力激盪、在XD上想破頭設計頁面的種種，這些回憶都是前所未有的經歷，謝謝PDIS提供這個機會，讓我的暑假有精彩的生活！