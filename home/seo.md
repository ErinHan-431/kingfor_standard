---
title: 搜尋引擎優化（SEO）
---
網站最主要目的就是有使用者前往瀏覽、使用服務。操作 SEO 能夠讓網站：

-   提高搜尋結果排名，出現在結果列表更前面位置。
-   提高網站曝光量，增加被看見的機會。
-   增加點擊率，產生更多商業效益。

## URL

一個簡潔、有意義的網址，除了提升 SEO 排名外，還能夠容易被使用者記住，甚至分享推廣時也能比較好看。

### 使用 `https://`

從資訊安全角度來說，所有網站盡可能使用 HTTPS 進行傳輸。

### 以首頁為規劃導覽功能的基準

建立網站的結構層次可以透過組織實體檔案，或使用路由等方法實現。從首頁開始計劃網站的導覽和階層，明確的階層結構有助於更容易理解單一網頁在整個網站架構中的位置。

建立自然而清楚流暢的階層，適當的分類也可以讓使用者更容易瀏覽，但也不要過度細分內容，導致使用者要多次點選連結才能從首頁到達所需頁面。

![範例階層圖](https://lh3.googleusercontent.com/FkXf1NMLRBDRD0-82WWHYCu7_nHxCzkUaMDFDAuGiFRYIrtgO3wqSJdtSFhpnyu3yeE=w314)<br />
圖、Google 提供的網站階層範例。

### 簡潔、有意義的網址

有意義的網址容易被使用者理解。舉例來說，下列網址就會讓使用者感到困惑，並產生不友善的感覺：

```
❌：https://www.brandonsbaseballcards.com/folder1/22447478/x2/14032015.html
```

應避免使用過長，或者包含不必要參數、工作階段 ID 的網址，減少被分享對象對連結網址的排斥：

```
❌：https://www.brandonsbaseballcards.com/item?id=E55C20F7-7B3E-4484-84B8-A6FBBE03C943
```

相較之下這段連結更為實用，搭配階層設計，在各種不同的情境中也更容易讓使用者理解：

```
✅：https://www.brandonsbaseballcards.com/article/ten-rarest-baseball-cards.html
```

![階層路徑與導覽標記](https://lh3.googleusercontent.com/iRXf8tJ7BTCs_Uwd4U2TgIKTXp_KOP8B-HGo-oqQ4ktQWdVQXKeZZbglL0QxOk6sdg=w650)<br />
圖、階層關係可以使用導覽標記顯示於畫面，也能夠表現於路徑中。

### 網址中的短標題

在網址中加入標題時，能使其更富意義，再加上網址支援中文字符，對於中文使用者更加友好。

但是，某些社交媒體平台的廣告功能（例如 Instagram）可能不支援中文網址，甚至在某些情況下，瀏覽器可能會將中文字符「善意地」轉換成 URL 編碼，導致分享連結變得冗長。

因此，除了直接把網頁標題放到網址外，可以另外準備欄位，讓使用者自行定義網址中的短標題，亦可加入 AI 協處產生。

### 重複內容

如果有多個頁面有相同內容，會造成內容信譽因分散而減弱。如要為 Google 搜尋重複或相似的網頁指定標準網址，例如桌面與行動裝置分版，可以透過多種方法指定偏好網址。這些方法依照對標準化的影響程度，排序如下：

-   重新導向：強烈的信號，表示重新導向的目標應成為標準網址。
-   `<link rel="canonical">` 註解：強烈的信號，表示指定的網址應成為標準網址。
-   納入 Sitemap：微弱的信號，可協助 Sitemap 包含的網址成為標準網址。

其中 `<link rel="canonical">` 用法為：

```HTML
<link rel="canonical" href="標準網址" />
```

### 重新導向

重新導向有區分永久與暫時兩種類型。

#### 永久重新導向

強烈訊號，在搜尋結果中顯示新目標，最能確保將 Google 搜尋和使用者導向正確網頁。

-   HTTP 301 (Moved Permanently)：表示所請求的資源已被永久地移動到新的位置，要求搜尋引擎更改索引記錄。
-   HTTP 308 (Permanent Redirect)：與 301 相同，但可以確保原始 HTTP 請求方法不會被改變。例如登入表單傳送位置從 `https://example.com/signup` 重定向到 `https://example.com/register`。

#### 暫時重新導向

微弱信號，在搜尋結果中顯示來源網頁，可以讓 Google 將搜尋結果中原本的網址保留較久。

-   HTTP 302 (Found)：表示所請求的資源已經暫時移動到新的位置。
-   HTTP 303 (See Other)：在重新導向後一律使用 GET 方法，不會使用原始的 POST、PUT，以避免將表單數據再次提交。例如表單送出後，重新導向至確認送出頁面。
-   HTTP 307 (Temporary Redirect)：重新導向時會沿用原始 HTTP 請求方法。像是主網站進行維護作業時，把表單傳送位置暫時導向至備援站點。

了解更多：[HTTP 狀態碼 - HTTP | MDN](https://developer.mozilla.org/zh-TW/docs/Web/HTTP/Status)。

### 404 頁面

有時候因為開啟無效連結或輸入錯誤的網址，而連至網站中不存在的網頁，利用 404 頁面協助使用者導向其他有效頁面，可以提升網站使用體驗。

404 頁面同樣需要加入索引，避免與網站完全不同的設計（如使用 IIS 等其他程式預設頁面），方便搜尋引擎辨識。

---

## 網頁摘要

搜尋引擎和社交媒體平台通常會顯示網頁資訊，提供一個質優的網頁摘要有助於確保內容呈現符合預期，同時提高使用者點擊連結前往瀏覽的意願。

了解更多：[Google 搜尋的視覺元素庫](https://developers.google.com/search/docs/appearance/visual-elements-gallery)。

### HTML head 元素

根據 HTML 標準，`<head>` 元素只能包含下列有效元素：

-   title
-   meta
-   link
-   script
-   style
-   base
-   noscript
-   template

除此之外，Google 只要偵測到任一無效元素，就會認定那是 `<head>` 元素的結尾，並停止讀取 `<head>` 元素中的任何後續元素。

### 網站名稱

Google 會從首頁中的結構化資料，或是 `og:site_name`、`<title>` 來解析網站名稱。其中，首頁是指網域或子網域層級的根 URI。舉例來說：

-   ⭕：https://example.com (這是網域層級首頁)
-   ⭕：https://www.example.com (這也被視為網域層級首頁)
-   ⭕：https://m.example.com (這也被視為網域層級首頁)
-   ⭕：https://news.example.com (這是子網域層級首頁)
-   ❌：https://example.com/news (這是子目錄層級首頁)

如果有內容相同的重複首頁（例如首頁同時擁有 HTTP 和 HTTPS 版，或 www 和非 www 版），請務必在所有重複的網頁上使用相同的結構化資料，而不只是標準網頁。

### 網頁標題

網頁標題主要使用 `<title>` 元素宣告。為了可以看出網站整體性，可以考慮在內容標題文字的開頭或結尾加入網站名稱，並以連字號、冒號或直立線做為分隔符號。如：

```HTML
<title>最新消息 - 奇豐資訊</title>
```

標題設計上，使用流暢易讀，而且可以有效傳達內容主題的標題文字，比起「新網頁 1」等預設或意義不明且與網頁內容無關的文字來說，會更吸引使用者點擊。同時也建議網站內盡量避免重複的標題，會讓使用者很難區分各網頁間有什麼不同。

Google 搜尋會使用下列來源自動判斷標題連結：

-   `<title>` 元素中的內容
-   網頁上顯示的主要標題元素 `<h1>`
-   指向該網頁的連結中使用的文字
-   WebSite 結構化資料

搜尋結果能夠顯示的字數有限，太長的標題會被截斷，因此建議標題總長度不超過 60 字元。

了解更多：[影響 Google 搜尋中的標題連結](https://developers.google.com/search/docs/appearance/title-link)。

### 描述

網頁的簡短描述或摘要，像是內容大綱，呈現於搜尋結果和社交媒體分享，幫助使用者了解該網頁的內容。可以使用 description 類型的 `<meta>` 元素或是結構化描述來宣告。

```HTML
<meta name="description" content="網頁內容描述">
```

提供欄位讓管理者編輯，也可以使用內容第一段落，或是配合 AI 協助生成。建議控制適量長度，確保能夠完整顯示，尤其是行動裝置版可顯示的內容有限。

了解更多：[管理搜尋結果摘要](https://developers.google.com/search/docs/appearance/snippet)。

### 社群連結摘要

社群媒體摘要對 SEO 優化沒有直接關係，但可以控制社群媒體分享時顯示的內容，吸引更多流量進入網站。例如 Facebook 分享時的文章標題：

```HTML
<meta name="og:title" content="文章標題">
```

以下列出 Facebook 常用到的 meta 類型：

| 類型           | 說明                                                                                                                                                 |
| -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| og:url         | 網頁的標準網址。這應是沒有任何修飾的網址，沒有工作階段變數、用戶識別參數或計數器。對此網址的按讚和分享應該匯總到此網址。                             |
| og:title       | 您文章的標題，不包含網站名稱等任何品牌內容。                                                                                                         |
| og:description | 內容的簡短說明，通常為 2 到 4 個句子，會顯示在 Facebook 貼文的標題下方。                                                                             |
| og:image       | 用戶將內容分享至 Facebook 時顯示的圖像網址。                                                                                                         |
| fb:app_id      | 若要使用 Facebook 洞察報告，您必須將應用程式編號新增至網頁。洞察報告可讓您從 Facebook 檢視您網站的流量分析。在您的應用程式主控板中尋找應用程式編號。 |

了解更多：[Facebook 網站管理員分享指南](https://developers.facebook.com/docs/sharing/webmasters)。

### robots

搜尋引擎會自動爬取可接觸的頁面，進行檢索與索引。但有些特殊頁面不希望出現在搜尋結果中，例如開發中或是網站後台等，便可利用 robots 類型的類型的 `<meta>` 元素設定 `noindex`。

若避免被品質不佳的外部連結降低 SEO 分數，也就是被低權威網站蹭權重，可以設定 `nofollow`，要求檢索程式不要對此頁面外部連結進行檢索。

```HTML
<!-- 項目之間用逗點(,)隔開 -->
<meta name="robots" content="noindex,nofollow">
```

如果是指定某個外部連結不要與網頁關聯，可以考慮在 `<a>` 元素加上 `rel="nofollow"`。

```HTML
<a href="https://www.mcdonalds.com/tw/zh-tw.html" rel="nofollow">
```

其中 `rel` 屬性可以接受的值有：

| 值        | 說明                                         |
| --------- | -------------------------------------------- |
| nofollow  | 請檢索程式忽略此外部連結。                   |
| sponsored | 該連結為網站廣告、贊助商。                   |
| ugc       | 這個連結是網站使用者建立的，不代表本站立場。 |

了解更多：[HTML attribute: rel](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes/rel)。

### 網站圖示

網站圖示可以利用 `<link>` 元素宣告：

```HTML
<link rel="icon" href="/path/to/favicon.ico">
```

### JSON-LD

可以使用 Schema.org 規範，透過 JSON-LD 語法建立 JSON 物件或陣列，以位於 HTML `<head>` 元素中的 `<script>` 標籤內的方式，將網頁資料結構嵌入網頁中。

```HTML
<script type="application/ld+json">
  {
    "@context" : "https://schema.org",
    "@type" : "WebSite",
    "name" : "Example",
    "url" : "https://example.com/"
  }
</script>
```

詳細請參閱：結構化資料 [Schema.org](schema.md)。

---

## Sitemap

Sitemap 是一種用來提交網站資訊的檔案，其中會列出網頁、影片以及其他檔案的資訊與彼此間的關係。Google 等多數搜尋引擎都會讀取網站的 Sitemap 檔案，藉此以更有效率的方式檢索網站。

單一 Sitemap 在未壓縮時的檔案大小上限為 50 MB，網址數量上限為 50,000 個。如果檔案大小或網址數量超過限制，則必須將您的 Sitemap 分割成數個 Sitemap。

### 文字 Sitemap

最簡單的 Sitemap 格式，只能列出 HTML 和其他可建立索引網頁的網址。

```
https://www.example.com/file1.html
https://www.example.com/file2.html
```

### XML Sitemap

XML Sitemap 是用途最廣泛的 Sitemap 格式，記載網站上有哪些網頁，也能用來提供圖片、影片和新聞內容相關額外資訊，再加上更新時間等詳細資訊，以及是否有其他語言版本。

```xml
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <url>
    <loc>http://www.example.com/</loc>
    <lastmod>2005-01-01</lastmod>
    <changefreq>monthly</changefreq>
    <priority>0.8</priority>
  </url>
</urlset>
```

可以用的 XML 標籤有：

| 標籤        | 必/選填  | Description                                                                    |
| ----------- | -------- | ------------------------------------------------------------------------------ |
| `<urlset>`  | required | Sitemap 文件主體，宣告此文件使用的協議標準。                                   |
| `<url>`     | required | 網頁 URL 的記錄主體。                                                          |
| `<loc>`     | required | 網頁網址，長度不可超過 2048 位元。                                             |
| `<lastmod>` | optional | 最後修改日期。應採用 W3C 日期時間格式，其中時間部份可以省略，如 `YYYY-MM-DD`。 |

如果 Sitemap 超過大小限制，就必須分割成多個文件，確保每個新的 Sitemap 都不超過大小限制。分割後可以使用 Sitemap 索引檔一次提交多個 Sitemap。

```xml
<?xml version="1.0" encoding="UTF-8"?>
<sitemapindex xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <sitemap>
    <loc>https://www.example.com/sitemap1.xml</loc>
  </sitemap>
  <sitemap>
    <loc>https://www.example.com/sitemap2.xml</loc>
  </sitemap>
</sitemapindex>
```

| 標籤             | 必/選填  | Description                                                                                                      |
| ---------------- | -------- | ---------------------------------------------------------------------------------------------------------------- |
| `<sitemapindex>` | required | XML 樹狀結構的上層標記，其中包含所有其他標記。                                                                   |
| `<sitemap>`      | required | 檔案中所列各個 Sitemap 的上層標記。這是 sitemapindex 標記的第一個且唯一的直接標記。                              |
| `<loc>`          | required | Sitemap 的位置 (網址)。這是 sitemap 標記的第一且唯一的子項。每個 Sitemap 索引檔最多只能包含 50,000 個 loc 標記。 |
| `<lastmod>`      | optional | 識別相應 Sitemap 檔案經過修改的時間。lastmod 標記的值必須採用 W3C 日期時間格式。                                 |

產出 Sitemap 雖然不會提升 SEO 成效與排名，但是可以讓 Google 快速了解網站架構，以及加快建立索引速度。也因此 Google 建議網站規模極大，網站的網頁數超過 500 個，或是才剛建立，幾乎沒有外部連結的網站，提交 Sitemap 來幫助 Googlebot 作業。

Sitemap 可以直接提交給搜尋引擎，也可以在 robot.txt 標記路徑，提供搜尋引擎檢索方向。

了解更多：[建立並提交 Sitemap](https://developers.google.com/search/docs/crawling-indexing/sitemaps/build-sitemap)。

---

## robot.txt

robots.txt 檔案能夠告訴搜尋引擎檢索器，網站上存在哪些網址與檔案，以及相關存取權限。網站只能有一個 robot.txt 檔案，必須存放於網域根目錄，必須是 UTF-8 編碼的文字檔案 (包括 ASCII)，否則可能會被忽略。

注意，這個檔案主要用來避免網站因要求過多而超載，**而不是讓特定網頁無法出現在 Google 搜尋結果**。

以資訊安全角度來說，如要防止指定網頁出現在搜尋結果，請使用 [noindex](#robots) 指令，避免在 robot.txt 文件中列出相關網址。而 robot.txt 文件可以改成用來記錄 Sitemap 所在位置。

### 註解

`#` 字元用來標示註解的起始處。在處理過程中，系統會忽略註解。

### User-agent

必要項目，標記規則群組適用的自動化使用者代理程式。

robots.txt 檔案可以包含數個規則群組，每個群組都會以一或多個 `User-agent:` 項目作為開頭，指定適用的使用者代理程式。使用星號 (\*) 表示對所有檢索器都適用。範例如下：

```
# Example 1: Block only Googlebot
User-agent: Googlebot
Disallow: /

# Example 2: Block Googlebot and Adsbot
User-agent: Googlebot
User-agent: AdsBot-Google
Disallow: /

# Example 3: Block all crawlers except AdsBot (AdsBot crawlers must be named explicitly)
User-agent: *
Disallow: /
```

系統會由上到下處理群組，每個使用者代理程式只能對應一組規則，也就是與其相應的第一組條件最明確的規則。如果同一個使用者代理程式有多個群組，系統會在處理前將這些群組合併為單一群組。

如果要為 Google 設定相關規則，請參閱 [Google 檢索器和擷取程式 (使用者代理程式) 總覽](https://developers.google.com/search/docs/crawling-indexing/overview-google-crawlers)。

### Allow / Disallow

每項規則至少要有一個 `Disallow:` 或 `Allow:` 項目，指出自動化程式「可以」或「不可」檢索哪些內容。但是，**該網址還是會被檢索程式得知，導致資安風險產生**！因此，要指定網頁不要被搜尋引擎檢索，請改用 [noindex](#robots) 指令。

根據預設，系統會允許使用者代理程式檢索未受 `Disallow:` 規則封鎖的網頁或目錄。

規則會區分大小寫，舉例來說：`disallow: /file.asp` 適用於 `https://www.example.com/file.asp`，但不適用於 `https://www.example.com/FILE.asp`。

### Sitemap

選用項目，指出網站的 Sitemap 所在位置，指出自動化程式「應該」檢索哪些內容。必須為完整網址。

Google 不會假設或檢查是否有 http/https/www/非 www 等替代網址。範例：

```
Sitemap: https://example.com/sitemap.xml
Sitemap: https://www.example.com/sitemap.xml
```

---

## 參考

-   [搜尋引擎最佳化 (SEO) 入門指南：基本概念 | Google 搜尋中心  |  說明文件  |  Google for Developers](https://developers.google.com/search/docs/fundamentals/seo-starter-guide)
