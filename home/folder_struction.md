# 專案資料夾結構

[![image.png](https://km.kingfor.com.tw/uploads/images/gallery/2026-08/scaled-1680-/image.png)](https://km.kingfor.com.tw/uploads/images/gallery/2026-08/image.png)

#### 資料夾結構

- `docs`: 專案中若需要特別的說明事項，可編寫文字檔、md檔，或是文件檔放在這裡。
- `build`: 專案中若有特別需要在CI/CD過程中作為建置用資源時，將其檔案放在這裡。
- `src`: 專案的原始碼，.sln及其原始碼階層放在這裡，單元測試碼亦放在這裡。
- `tests`: 專案的整合測試 (integrated tests) 碼。
- `data`: 執行整合測試時所需的測試資料。

#### 原始碼結構

- `Abstraction`: 專案的抽象定義
- `Client`: 用戶端 (包含 Web、Console、Tasks 等)
- `Domain`: 領域專案
- `Service`: 服務專案 (不屬於任何domain的程式) (盡量不要有，建議功能全數歸類於Domains底下做為領域控管)
- `Tests`: 單元測試專案 (整合測試放在Gitlab層級專案結構的`tests`內)
- `Utils`: 工具類專案 (於專案層級中作為共用的工具元件)