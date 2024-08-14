---
title: 一般性程式命名準則
---
程式碼的**可讀性 (readability)** 與**可理解性 (understandable)** 是程式開發的基本要求，身為開發團隊的一員，對程式碼的可讀性必須自我要求，以讓團隊的其他成員能夠適時支援，或是在人員因請假、離職等因素下能夠順暢的讓其他團隊成員接手，同時亦可以讓自己在日後因維護該程式而回頭檢視時，能更快的理解與上手。

> 程式碼的可讀性是提升團隊效能的其中一個因素。

##	**區域變數之命名，以小寫英文字元為首字元，除迴圈之增量或減量子可用單一字母外，應可反應實際用途。**

變數 (variable) 的主要作用是在保留資料，以供後續運算處理之用，若是使用了模糊不清的名稱，則必須要經由適當的追踪 (trace) 與確認才可以認定這個變數的工作，它可能不會花太多時間，但是累積下來也可能是相當可觀的時間成本，因此減少這類時間成本是非常容易的事，只要一開始就把名稱命名好。

以下列需求來說：

> 設計一支程式，傳入應計稅率與淨所得收入，回傳應繳納稅金額。應繳納稅額為淨所得收入乘以應計稅率。

下列程式碼的命名就不洽當：

```csharp
var r = 0.05;
var na = 1500000;
var a = r * na;
```

下列程式碼的命名就很洽當：

```csharp
var taxRate = 0.05;
var taxableAmount = 1500000;
var taxAmount = taxRate * taxableAmount;
```

日後再回來維護或調整程式時，清晰的命名將會有助於快速理解，省去確認的麻煩，也不容易出錯。

然而，若是在極有限的範圍內 (例如迴圈)，其增量子 (imcrement operator) 或減量子 (decrement operator) 在不影響整體可讀性的情況下，可適度使用單一字母的變數名稱，但若迴圈內的增量子或減量子有可識別的意義時，仍然建議採用清晰的命名為宜。

##	**類別層級變數之命名，除依區域變數之命名外，首字元必須為底線 (“_”)。**

類別層級變數，一般稱為欄位 (field) 或成員變數 (member variable)，其作用範圍在類別層級，這意味著它會跨越不同的方法或屬性，為了要能**明確識別其範圍**，故首字元以底線為首。

例如：

```csharp
public class TaxCalculator
{
    private double _taxRate = 0.05;

    public decimal CalculateTaxAmount(decimal taxableAmount)
    {
        return _taxRate * taxableAmount;
    }
}
```

會比

```csharp
public class TaxCalculator
{
    private double taxRate = 0.05;

    public decimal CalculateTaxAmount(decimal taxableAmount)
    {
        return taxRate * taxableAmount;
    }
}
```

更容易辨識變數是屬於哪個層級的。

Reference: <br />
https://www.dofactory.com/csharp-coding-standards#nounderscores <br />
https://www.c-sharpcorner.com/UploadFile/8a67c0/C-Sharp-coding-standards-and-naming-conventions/

##	**函數或方法之命名，以大寫英文字元為首字元，且應能反應該函數或方法執行的動作。**

函數或方法為執行程式動作之基本單元，因此命名上應使用反應其動作的名稱 (以動詞或可表示執行動作之意思為主)，不應使用不相關或是會混淆其動作意涵的名稱，函數或方法採用 Pascal 命名規則。

例如，一個執行檔案上傳的方法，應如此命名：

```csharp
public void UploadFile(string name, byte[] fileData) 
{
    // ... file upload
}
```

而不是這樣命名：

```csharp
// Method1 不明其意
public void Method1(string name, byte[] fileData) 
{
    // ... file upload
}
// 有誤導可能，除非類別名稱可以輔助其辨識
public void Write(sting name, byte[] fileData)
{
    // ... file upload
}
```

##	**屬性之命名，以大寫英文字元為首字元，且應能反應該屬性對應之資料類型。**

屬性 (Property) 為類別成員之一，作用為保存類別所需資料，並作為外界與內部資料的溝通橋樑之一，因此其命名應能反應所保存的資料與其用途，屬性命名採用 Pascal 命名規則。

例如：

```csharp
private double _taxRate = 0.05;

// 傳統寫法
public double TaxRate 
{
    get { return _taxRate; }
    set { _taxRate = value; }
}

// C# 6.0 起寫法
public double TaxRate { get; set; }
```

而不是

```csharp
private double _r = 0.05;

public double R 
{
    get { return _r; }
    set { _r = value; }
}
```

##	**類別名稱之命名，以大寫英文字元為首字元，且應以該類別所負責之領域範圍或功能命名。**

類別為封裝一系列行為與資料，以處理特定服務或功能要求為物件，其命名應以其負責的領域 (domain) 或功能 (feature) 命名之，類別命名採用 Pascal 命名規則。

##	**列舉與常數之命名，以大寫英文字元為首字元，且應可反應實際用途。**

列舉 (enum) 與常數 (const) 用途相似，列舉係以整數為基底順序排列之值集合 (預設為int，由0開始)，常數則是可以自訂的名稱替代數值，以避免魔術數字 (magic number) 的產生，因此其命名原則為以 Pascal 命名規則，則時應反應出該列舉或常數之用途。

列舉型別名稱宜採用單數名稱，且不需加入後綴字，例如：

```csharp
// OK
public enum ImageType
{
    Gif,
    Jpeg,
    Png
}
// Don't
public enum ImageTypeEnum
{
    Gif,
    Jpeg,
    Png
}
```

常數則考慮到其範圍較廣，因此雖然它會是類別的成員之一，但不以成員變數的方式命名，而是使用與類別相同的命名法則，但要注意的是，不宜以全部大寫字元方式命名，也不要因為有多個單字而用底線切分。

```csharp
// OK
public const string DefaultImageType = "Gif";
// Don't
public const string DEFAULTIMAGETYPE = "Gif";
// Don't
public const string DEFAULT_IMAGE_TYPE = "Gif";
```

Reference:  <br />
https://www.dofactory.com/csharp-coding-standards#constants

##	**如以多個英文單詞描述時，應將單詞以首字大寫方式連接，但第一個字元仍應依上列要求設定；單詞宜避免使用超過三個；如命名超過20字元時，宜考慮使用縮寫，**

當變數、方法、屬性等會以兩個字詞 (2 words) 以上命名時，除前述之命名方針外，第一個字詞的首字母依命名方針設定大寫或小寫，第二個字以後採用首字大寫，例如：

* 類別：UserService
* 變數：_userService (類別變數) 或是 userService (區域變數)
* 方法：SubmitFile()

為避免名稱過長，單詞宜避免超過三個，若會超過3個單詞但長度小於20時亦可接受，但若會超過20字元時，宜考慮使用縮寫，縮寫 (abbreviation) 亦應使用領域範圍內公認的縮寫，如沒有可公認縮寫時，應在變數宣告時加上註解。


> 若無法找到適當縮寫或是使用縮寫會使其辨識度下降時，則可與團隊主管討論確定如何命名。

```csharp
private RNGCryptoServiceProvider _randomNumberGenerator; // 隨機數產生器
private RNGCryptoServiceProvider _ranNumGenerator; // 隨機數產生器 (Random Number Generator)
private RNGCryptoServiceProvider _rng; // 隨機數產生器 (Random Number Generator)
```

## **多個單詞連接時，除非特別必要並加上註解外，不可使用底線 (“_”) 連接。**

如命名需要多個單詞連接，使用首字大寫區隔即可，不應使用底線，以避免輸入困擾。

例如：

```csharp
// OK
private RNGCryptoServiceProvider _randomNumberGenerator; // 隨機數產生器
// Don't
private RNGCryptoServiceProvider _random_Number_Generator; // 隨機數產生器
```

##	**縮寫的使用以名詞之通用、標準或業界慣例為主，如有專業術語時以術語為優先。**

如果需要使用到縮寫，則應盡量使用業界標準或產業認可的縮寫字。

##	**不可使用匈牙利命名法 (Hungarian notation) 與使用中文命名。**

因現代程式語言命名已不如早期會影響記憶體的可用容量，故不再需要使用加上型態前綴字的匈牙利命名法。

另外，使用中文命名會限制程式碼的流通範圍 (與非華人的外國工程師合作時)，且在輸入時需要更多習慣 (如流暢的中文輸入法切換)，否則不利於程式碼的生產力。