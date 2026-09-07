---
title: 程式設計典範
---
## SOLID 原則

### **單一職責原則 (Single Responsibility Principle/SRP)**

> 永遠不應該因為多一個理由去改變一個類別。每個類別應該有各自的責任，而這個責任應該完全被封裝在類別中。因為一個理由改變可以定義責任，所以類別或模組應該有一個或只有一個改變的理由。

### **開放封閉原則 (Open-Close Principle/OCP)**

> 軟體實體(例如類別)應該開放擴充，但對修改封閉:對模組進行擴展時,原本正確之部分不該被變更，也就是實體可以允許在沒有修改源程式碼下修改它的行為。

### **里式替換原則 (Liskov's Substitution Principle/LSP)**

> 子類別物件能夠替換作基礎類別（base class或super class）物件被使用。

### **介面隔離原則 (Interface-Separation Principle/ISP)**

> 減少肥胖的介面到多個更小更特別的特殊介面。一個界面應該依賴呼叫它的程式碼更勝於實作它。

### **相依反轉原則 (Dependency Inversion Principle/DIP)**

> 相依於抽象而非相依於實作。

## 其他重要典範

下表為物件導向程式設計中許多較重要的典範，大致都與 SOLID 類似，但部份會有較細微的指南，可閱讀參考連結以得到更多資訊。

|典範|說明|參考連結|
|---|---|---|
|KISS (Keep It Simple, Stupid)|大部份的系統保持簡單比複雜更好。|[維基百科](https://zh.wikipedia.org/wiki/KISS%E5%8E%9F%E5%88%99)|
|YAGNI (You aren't Gonna Need It)|**不過度設計**，你真的沒那麼需要它：除非真的必要，否則不應該實作它。|[Martin Fowler blog](https://martinfowler.com/bliki/Yagni.html)<br />[維基百科](https://zh.wikipedia.org/zh-tw/YAGNI)|
|Do The Simplest Thing That Could Possibly Work|盡可能以最簡單的方式達成任務。|[DEV Community](https://dev.to/scottshipp/the-simplest-thing-that-could-possibly-work-d6j)|
|Separation of Concerns|**關注點分離**，區分電腦程式到不同區塊的設計原則，使得每一區塊呼叫個別的關注點。|[維基百科](https://zh.wikipedia.org/zh-tw/%E5%85%B3%E6%B3%A8%E7%82%B9%E5%88%86%E7%A6%BB)<br />[NDepend blog](https://blog.ndepend.com/separation-of-concerns-explained/)|
|DRY (Don't Repeat Yourself)|**不重覆實作**，每一個知識必須在系統內單一、明確、表示權威性。|[維基百科](https://zh.wikipedia.org/zh-tw/%E4%B8%80%E6%AC%A1%E4%B8%94%E4%BB%85%E4%B8%80%E6%AC%A1)<br />[Avoiding Reptition](https://martinfowler.com/ieeeSoftware/repetition.pdf)|
|Code For The Maintainer|站在維護程式碼的人的角度編寫程式。|[Rule #5 - Code for the Maintainer](https://www.cambiaresearch.com/articles/79/rule-5---code-for-the-maintainer)|
|Avoid Premature Optimization|避免過早優化。|[Premature Optimization: Why It’s the “Root of All Evil” and How to Avoid It](https://effectiviology.com/premature-optimization/)|
|Minimize Coupling|**低耦合**，模組與組件之間的互相依賴愈少愈好。|[維基百科](https://zh.wikipedia.org/wiki/%E8%80%A6%E5%90%88%E6%80%A7_(%E8%A8%88%E7%AE%97%E6%A9%9F%E7%A7%91%E5%AD%B8))|
|Maximize Cohesion|**高內聚**，凝聚單一模組或組件的負責程度是有意義的，凝聚力越高越好。|[維基百科](https://zh.wikipedia.org/wiki/%E5%85%A7%E8%81%9A%E6%80%A7)|
|Law of Demeter|不要跟陌生人說話。|[維基百科](https://zh.wikipedia.org/zh-tw/%E5%BE%97%E5%A2%A8%E5%BF%92%E8%80%B3%E5%AE%9A%E5%BE%8B)|
|Composition Over Inheritance|組合優於繼承。|[維基百科](https://en.wikipedia.org/wiki/Composition_over_inheritance)|
|Orthogonality|**正交性**，概念中不相關的東西不應該在系統上有關聯。|[維基百科](https://en.wikipedia.org/wiki/Orthogonality_(programming))|
|Robustness Principle|在你做事時保持保守，在你接收其它事時保持自由。|[維基百科](https://en.wikipedia.org/wiki/Robustness_principle)|
|Hide Implementation Details|一個軟體模組隱藏資訊(即實作細節)提供一個介面，而不泄露任何不必要的資訊。|[維基百科](https://en.wikipedia.org/wiki/Information_hiding)|
|Curly’s Law|關於對任何特定程式碼只選擇單一，清楚定義目標：只做一件事。|[Curly's Law: Do One Thing](https://blog.codinghorror.com/curlys-law-do-one-thing/)|
|Encapsulate What Changes|**封裝變更**，好的焦點辨識設計就像是改變和封裝在API內。當預期發生變化時，保持原狀調整。|[Encapsulate the Concept that Varies (ECV)](http://principles-wiki.net/principles:encapsulate_the_concept_that_varies)|
|Boy-Scout Rule|保持程式碼比我們發現它時更整潔。|[The Boy Scout Rule](https://www.informit.com/articles/article.aspx?p=1235624&seqNum=6)|
|Command Query Separation|一個分法應該區分命令執行動作或查詢回饋資料給呼叫者，而不是兩個一起。問一個問題不應該修改答案。|[Martin Fowler blog](https://martinfowler.com/bliki/CommandQuerySeparation.html)|