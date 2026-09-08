# 組件結構

## 簡述

過往的架構，大多像是一顆大泥球一樣相互混砸在一起，往往會造成功能與功能間的過耦合，導致改一個壞一個的事情屢屢發生

要改善這個問題，必須得從結構著手；讓各個領域間可以有更清楚的邊界，並確保領域內部狀態的合規。

簡潔架構 ∇

[![Clean_Architecture.png](https://km.kingfor.com.tw/uploads/images/gallery/2025-12/clean-architecture.png)](https://km.kingfor.com.tw/productdevteam/kfox30/kfox30/-/wikis/uploads/129aad50b77b0ec8b7ffd38875d59419/Clean_Architecture.png)

組件組合 ∇

[![20111997h9GLLdfFTU.jpg](https://km.kingfor.com.tw/uploads/images/gallery/2025-12/20111997h9glldfftu.jpg)](https://km.kingfor.com.tw/productdevteam/kfox30/kfox30/-/wikis/uploads/c0752313d5936ab895e0c3dab5263ae8/20111997h9GLLdfFTU.jpg)

優點：

- 集中的領域邏輯(業務邏輯)
- 永遠合規的狀態
- 如積木般組合的架構

缺點：

- 區分過多專案，導致客制專案開發負擔

## [](#%E5%8A%9F%E8%83%BD%E7%B5%90%E6%A7%8B)功能結構

主要分為四個專案(亦可更多)：

- Domain 
    - 負責領域邏輯(商業邏輯)的一致性維護
- Infrastructure 
    - 負責Domain中定義行為的實現
- Abstraction / Contracts 
    - 對外抽象，主要處理該組件對外暴露的方法的Interface
- Application 
    - 領域對外窗口
    - 負責流程控制

[![DDD開發架構概念.png](https://km.kingfor.com.tw/uploads/images/gallery/2026-07/ddd.png)](https://km.kingfor.com.tw/productdevteam/kfox30/kfox30/-/wikis/uploads/f407a664c27b693211c77b5f158d8a11/DDD-%E5%8A%9F%E8%83%BD%E6%9E%B6%E6%A7%8B.png)

## [](#domain)Domain

為該領域核心，制定並維護聚合(Aggregate)

至少需具備以下兩種功能：

- 建立
- 重建

其中**建立**為將一聚合從無到有的建構，**建立**過程亦包含領域邏輯。

**重建**則為重新建立一個已存在的聚合，通常為自將資料庫取出之資料轉為聚合之動作。

於Domain中，亦會制定對於Repository之interface，規範持久化之動作

甚至於列舉(Enums)、IUnitOfWork、分頁物件皆定義於Domain層內部，資料傳遞到外不時透過中轉轉換成外部所需格式；但考慮到專案實做面的問題，可允許Domain關聯至Abstrations，但其二者之層級為平行關係，非上下級

### [](#%E8%81%9A%E5%90%88)聚合

為領域**內部**的最小單位，任何動作皆必須透過聚合進行。

無論是建立或是重建，聚合都將維護自身的**合規性**，任何動作皆需通過聚合，聚合將維護自身所必要之檢查。

聚合本身代表「**唯一真實的商業概念**」，故不應進行抽象化，且會鎖在組件內部，不會對外暴露

[![DDD-傳遞物件.png](https://km.kingfor.com.tw/uploads/images/gallery/2025-12/ddd.png)](https://km.kingfor.com.tw/productdevteam/kfox30/kfox30/-/wikis/uploads/28db46a5425d1dd5c8bb09fbbe257dd4/DDD-%E5%82%B3%E9%81%9E%E7%89%A9%E4%BB%B6.png)

### [](#domain-service)Domain Service

領域服務，位於Domain層，但不一定會存在。

主要職責為協調各種需橫跨多個Aggregate的領域邏輯，但不應使用到外部服務。

### [](#domain-event)Domain Event

領域事件，通常由聚合或Domain Service所產生，並透過Application Service發布

依照影響區域可大致分為兩種：內部事件、外部事件

內部與外部事件亦透過Application分隔或散播，亦即Application可再接收內部事件後，將其轉換為外部事件發送

## [](#repository)Infrastructure

基礎建設層，負責實現Domain中所定義的行為，如：聚合的持久化儲存

不參與任何領域邏輯之運算

### Repository

一個Domain中可具備多個Repository，一個Aggregate資料亦可能來源於多個Repository

對於需要多個異質Repository協作之情況，可由一工廠(Factory)進行多個聚合間之協調

[![DDD-Repository.png](https://km.kingfor.com.tw/uploads/images/gallery/2025-12/ddd-repository.png)](https://km.kingfor.com.tw/productdevteam/kfox30/kfox30/-/wikis/uploads/48fcb142b7478eb327bcdc62ab2874e8/DDD-Repository.png)

## [](#application)Application

應用層，定義功能要完成之業務/使用案例(Use Case)，負責流程上的控制與各內部聚合間的協調。

**Domain**層**聚合**的真正使用者，由Infrastructure取得聚合後，依據**聚合**提供之功能進行聚合操作，最後再透過Infrastructure持久化

Application亦為領域對外開放之功能，為領域之邊界；並可整合外部不同領域之功能，以此達成任務。

[![DDD-Application流程.png](https://km.kingfor.com.tw/uploads/images/gallery/2025-12/ddd-application.png)](https://km.kingfor.com.tw/productdevteam/kfox30/kfox30/-/wikis/uploads/15f62e1cba2eb8a14c2d453e64015a9d/DDD-Application%E6%B5%81%E7%A8%8B.png)