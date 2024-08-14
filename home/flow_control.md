---
title: 流程控制與條件判斷
---
## ```if…else…```條件式

### **巢狀```if…else…```宜以不超過三層為原則，如可能會超過三層時，應將其改寫為函數，以降低複雜度。**

當條件判斷出現多條件漸次判斷的需要時，會出現巢狀 (nested) 的寫法，但是應該將巢狀的層次數控制在三層以內，避免波動拳的寫法出現，這會阻礙程式的可讀性與可維護性。

這個就是 if 波動拳：

![if 波動拳](uploads/7ba2c456618fd9ae30d152022c5350e8/2023-04-21-10-33-19.png)

>   若是可能會出現三層以上的巢狀判斷時，建議可採用下列幾種方式：
>
>   1. 將判斷切出為函數，於函數中判斷。
>   2. 使用責任鏈模式 (Chain of Responsibility) 切割，將判斷作業交由各個負責的類別處理。

### **單層```if…else…```回傳資料之條件判斷，可使用簡化條件運算式 (```..? .. : ..```) 簡化程式碼。**

一般來說，若是下列這種型式的`if...else`判斷：

```csharp
int amount;

if (isVip)
{
    amount = amount * 0.9;
}
else
{
    amount = amount * 0.95;
}
```

可簡寫成以`?:`表示的程式碼，可簡化複雜度。

```csharp
int amount = amount * (isVip ? 0.9 : 0.95);
```

### **檢查```null```的條件判斷可使用```null```檢查條件運算式 (```??```) 簡化程式碼。**

若是使用`nullable`型別的資料做`null`的判斷時，若是這樣的寫法：

```csharp
DataTable table = GetAdminList();
string id;

if (table != null)
    id = table.Rows[0]["ID"].ToString();
else
    id = "empty";
```

可以改用這樣的寫法來簡化：

```csharp
DataTable table = GetAdminList();
string id = table?.Rows[0]["ID"].ToString() ?? "empty";
```

### **`if`內的條件應控制在一定程度 (如三個以內)，若是有太多條件要判斷，可將判斷式切到一個函數**

請思考下列程式：

```csharp
if (a = 1 && b = 2 && c = 3 && d = 4 && e = 5 && f = 6)
{
  ...
}
else 
{
  ...
}
```

在同一個`if`內的判斷式過多，容易造成可讀性問題，若同時裡面又包含`OR`，出錯的可能性亦會提高，這時候可考慮將判斷切到一個函數來執行，能提升可讀性，也比較不容易出錯，尤其是在具有流程性質的功能，這類功能通常會有大量的條件判斷。

```csharp
if (IsValid(a, b, c, d, e, f))
{
  ...
}
else 
{
  ...
}

bool IsValid(int a, int b, int c, int d, int e, int f) => a = 1 && b = 2 && c = 3 && d = 4 && e = 5 && f = 6;
```


## ```switch case```條件式 

### **除判斷為列舉型態，且所有列舉值都有被檢查外，```switch case```實作應包含```default```陳述式，以處理在預期外的值範圍。**

`switch case` 會依據 `case` 所指定的值進行逐項檢查，若沒有符合 `case` 定義的，會由 `default` 來執行，因此原則上所有 `switch case` 都應包含 `default` 並實作不符合所有 `case` 值條件時要處理的作業，但若檢查的型態是列舉型態，而且所有的列舉值都有被處理到時則不在此限。

> Visual Studio 內的程式碼分析工具會在 `switch case` 沒有 `default` 時會給提示。

### **如處理的方式相同時，```case```應置於同一處，避免重覆的程式碼。**

例如下列這種情況：

```csharp
bool? isChecked = null;

switch (checkValue)
{
  case 1:
      isChecked = true;
      break;
  case 2:
      isChecked = true;
      break;
  case 3:
      isChecked = false;
      break;
  default:
      break;
}
```

可以寫成這樣，以簡化程式碼：

```csharp
bool? isChecked = null;

switch (checkValue)
{
  case 1:
  case 2:
      isChecked = true;
      break;
  case 3:
      isChecked = false;
      break;
  default:
      break;
}
```

### **如```switch case```條件具複雜度時，可考慮使用Pattern Matching方式編寫條件式。**

由於`switch case`只能支援單一值的判斷，若是要在`switch case`中使用多重條件，一般只能在`case`中編寫其他判斷式。在 C# 9.0 開始提供了模式比對 (Pattern Matching) 的作法，可以使用運算式來處理```switch case```，如下列程式：

```csharp
public decimal CalculateDiscount(Order order) =>
    order switch
    {
        ( > 10,  > 1000.00m) => 0.10m,
        ( > 5, > 50.00m) => 0.05m,
        { Cost: > 250.00m } => 0.02m,
        null => throw new ArgumentNullException(nameof(order), "Can't calculate discount on null order"),
        var someObject => 0m,
    };
```

Reference:
[Pattern matching overview](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/functional/pattern-matching)