# 版本控制規範與政策（2026）

##### 一、制度目的（Scope）

本制度旨在規範 DTD 技術團隊於專案開發、維運與緊急修復過程中的 Git 版本控制行為，  
透過一致的分支架構、合併審核機制與提交規範，確保：

1. 程式碼歷史具備**完整性、可追溯性與不可竄改性**
2. 專案開發流程**可控、可審核、可交接**
3. 正式環境（Production）之系統穩定性與版本一致性
4. 緊急修復與功能開發在速度與品質之間取得平衡

---

##### 二、適用範圍（Scope）

1. 本制度適用於 **DTD 技術部所有 Git Repository**
2. 適用對象包含： 
    - DTD 全體工程師
    - 專案技術負責人（Tech Lead）
    - GitLab 平台管理者
3. 凡涉及以下情境，皆須遵循本制度： 
    - 新功能開發
    - 專案交付與版本發佈
    - 正式環境維運與客服修復
    - 緊急 Hotfix 處理

---

##### 三、分支架構與公司環境對應

3.1 主分支定義

<div class="group TyagGW_tableWrapper flex w-fit flex-col-reverse" id="bkmrk-%E5%88%86%E6%94%AF%E5%90%8D%E7%A8%B1-%E8%A7%92%E8%89%B2%E5%AE%9A%E7%BE%A9-%E5%B0%8D%E6%87%89%E7%92%B0%E5%A2%83-%E9%80%B2%E5%85%A5%E6%A2%9D%E4%BB%B6-" tabindex="-1"><table class="w-fit min-w-(--thread-content-width)" data-end="849" data-start="620"><thead data-end="649" data-start="620"><tr data-end="649" data-start="620"><th data-col-size="sm" data-end="627" data-start="620">分支名稱</th><th data-col-size="sm" data-end="634" data-start="627">角色定義</th><th data-col-size="sm" data-end="641" data-start="634">對應環境</th><th data-col-size="sm" data-end="649" data-start="641">進入條件</th></tr></thead><tbody data-end="849" data-start="668"><tr data-end="735" data-start="668"><td data-col-size="sm" data-end="677" data-start="668">master</td><td data-col-size="sm" data-end="701" data-start="677">Production-Ready（維護版）</td><td data-col-size="sm" data-end="708" data-start="701">正式環境</td><td data-col-size="sm" data-end="735" data-start="708">僅能由 staging 合併，且須完成 UAT</td></tr><tr data-end="795" data-start="736"><td data-col-size="sm" data-end="746" data-start="736">staging</td><td data-col-size="sm" data-end="770" data-start="746">Pre-release / RC（測試版）</td><td data-col-size="sm" data-end="781" data-start="770">測試／預發佈環境</td><td data-col-size="sm" data-end="795" data-start="781">僅能由 dev 合併</td></tr><tr data-end="849" data-start="796"><td data-col-size="sm" data-end="802" data-start="796">dev</td><td data-col-size="sm" data-end="821" data-start="802">Integration（開發版）</td><td data-col-size="sm" data-end="828" data-start="821">開發環境</td><td data-col-size="sm" data-end="849" data-start="828">Feature 驗收完成後之整合點</td></tr></tbody></table>

</div>3.2 主分支定位說明

- **master（維護版）**  
    已進入數位生命周期之專案主線，為客服維運與正式系統唯一依據。
- **staging（測試版）**  
    作為技術、專案管理與政策、里程碑整合測試之關鍵分支。
- **dev（開發版）**  
    全新功能與數位生命周期專案之主要整合開發分支。

---

##### 四、分支基準與維護規範

4.1 分支基準來源

1. **新功能開發**： 
    - 必須自 `dev` 分支切出
2. **緊急修復（Hotfix）**： 
    - 僅能自 `master` 或指定之 `staging` 分支切出

---

4.2 程式碼歷史完整性（強制條款）

1. **嚴禁強制推送（Force Push）**
    - 禁止使用 `-f`、`--force`
    - 遠端 Commit 紀錄不得被重寫或抹除
2. **錯誤還原規範**
    - 已推送至遠端之 Commit 如需撤銷： 
        - 必須使用 `git revert`
        - 嚴禁使用 `git reset` 回寫歷史
3. **主分支操作限制**
    - 嚴禁直接於 `master`、`staging`、`dev` 進行 Commit
    - 僅允許： 
        - Merge Commit
        - 解衝突 Commit

---

4.3 專案初始化與版本一致性

1. **新專案初始化**
    - 必須先於 `master` 完成系統初始化
    - 再切出 `dev` 與 `staging`
2. **正式環境一致性**
    - `master` 分支程式碼 Hash 值  
        必須與客戶正式環境 **100% 一致**

---

##### 五、合併與審核機制（Merge Request, MR）

5.1 強制審核制度

<div class="group TyagGW_tableWrapper flex w-fit flex-col-reverse" id="bkmrk-%E7%9B%AE%E6%A8%99%E5%88%86%E6%94%AF-%E5%AF%A9%E6%A0%B8%E8%A6%8F%E7%AF%84-master-%2F-s" tabindex="-1"><table class="w-fit min-w-(--thread-content-width)" data-end="1799" data-start="1689"><thead data-end="1704" data-start="1689"><tr data-end="1704" data-start="1689"><th data-col-size="sm" data-end="1696" data-start="1689">目標分支</th><th data-col-size="sm" data-end="1704" data-start="1696">審核規範</th></tr></thead><tbody data-end="1799" data-start="1715"><tr data-end="1763" data-start="1715"><td data-col-size="sm" data-end="1734" data-start="1715">master / staging</td><td data-col-size="sm" data-end="1763" data-start="1734">必須由 GitLab 負責人或授權 Lead 審核</td></tr><tr data-end="1799" data-start="1764"><td data-col-size="sm" data-end="1770" data-start="1764">dev</td><td data-col-size="sm" data-end="1799" data-start="1770">可由工程師進行 Peer Review 後自行合併</td></tr></tbody></table>

</div>---

5.2 合併層級規則（強制）

1. **標準流程**  
    `dev → staging → master`
2. **禁止事項**
    - 嚴禁跨級合併（如 dev → master）
    - 所有功能必須先於 `staging` 完成整合測試

---

5.3 MR 准入條件

以下情況 **不得發起 MR**：

- 功能未完成
- 測試失敗
- Lint 或 CI 檢查未通過

---

5.4 同步與後續修正

1. **基準同步**
    - 若 Base 分支更新，主題分支須主動 Merge 更新
    - 衝突需於本地先行解決
2. **合併後修正**
    - 原則上於原主題分支修正後重新發起 MR

---

##### 六、提交品質與命名規範

6.1 原子化提交原則

- 每一個 Commit： 
    - 僅處理一個主題
    - 功能完整、目的明確
    - 避免混合多項修改

---

6.2 語意化 Commit 規範（Conventional Commits）

**格式：**

<div class="overflow-y-auto p-4" dir="ltr" id="bkmrk-%3Ctype%3E%3A-%3Cdescription">`<span class="language-xml"><span class="hljs-tag"><<span class="hljs-name">type</span></span></span>>: <span class="hljs-tag"><<span class="hljs-name">description</span></span>> (#IssueID)`</div>**Type規範：**

- feat: 新增/修改功能 (feature)。
- fix: 修補 bug (bug fix)。
- docs: 文件 (documentation)。
- style: 格式 (不影響程式碼運行的變動 white-space, formatting, missing semi colons, etc)。
- refactor: 重構 (既不是新增功能，也不是修補 bug 的程式碼變動)。
- test: 增加測試 (when adding missing tests)。
- chore: 建構程序或輔助工具的變動 (maintain)。
- revert: 撤銷回覆先前的 commit 例如：revert: type(scope): subject (回覆版本：xxxx)。
- packages: 套件版本更新。
- ci: CICD腳本異動。

**範例：**

- `feat: 新增會員登入功能 (#45)`
- `fix: 修正購物車金額計算錯誤 (#102)`

---

6.3 版本標記（Tagging）

- 專案里程碑（UAT、正式上線）： 
    - 必須於 `master` 標註 Git Tag
- 範例： 
    - `v1.2.0`

---

##### 七、緊急修復（Hotfix）制度

7.1 適用定義

僅適用於以下情境：

- 正式環境重大 Bug
- 系統服務中斷或影響營運之問題

---

7.2 快速修復路徑

**方式一：由 master 切出**

<div class="sticky top-[calc(--spacing(9)+var(--header-height))] @w-xl/main:top-9" id="bkmrk--15"><div class="absolute end-0 bottom-0 flex h-9 items-center pe-2"><div class="bg-token-bg-elevated-secondary text-token-text-secondary flex items-center gap-4 rounded-sm px-2 font-sans text-xs">  
</div></div></div><div class="overflow-y-auto p-4" dir="ltr" id="bkmrk-fix-%5B%E5%AE%A2%E6%9C%8D%E6%88%96%E8%AD%B0%E9%A1%8C%E7%B7%A8%E8%99%9F%5D">`fix-<span class="hljs-selector-attr">[客服或議題編號]</span>`</div>範例：

- `fix/CS-2024001`
- `fix/99-Hotfix`

**方式二：由 staging 切出（專案型）**

<div class="sticky top-[calc(--spacing(9)+var(--header-height))] @w-xl/main:top-9" id="bkmrk--16"><div class="absolute end-0 bottom-0 flex h-9 items-center pe-2"><div class="bg-token-bg-elevated-secondary text-token-text-secondary flex items-center gap-4 rounded-sm px-2 font-sans text-xs">  
</div></div></div><div class="overflow-y-auto p-4" dir="ltr" id="bkmrk-staging-%5B%E5%B0%88%E6%A1%88%E7%B7%A8%E8%99%9F%5D-hotfi">`staging-<span class="hljs-selector-attr">[專案編號]</span>-hotfix-<span class="hljs-selector-attr">[問題簡述]</span>`</div>---

7.3 回補規範（強制）

1. 修復完成後： 
    - 發起 MR 至 `staging` 驗證
2. 驗證通過： 
    - 合併至 `staging`
    - **必須同時合併回 `dev`**
3. 目的： 
    - 防止 Bug 於下次改版再次出現

---

##### 八、分支生命週期管理

8.1 原則

分支的存在，是為了解決一個明確問題  
問題解決，分支即應消失

8.2 分支並行

在專案中由於特定原因而需同時存在兩條源自同一上層且相互獨立的分支時

由於我方注機資源限制

故這兩條獨立分支的擁有者，應相互協調，避免相互搶佔測試資源的情況發生

---

8.3 清理規範

1. 功能合併並驗收完成後： 
    - 由合併者刪除主題分支
2. 無需額外申請
3. 可由系統自動清理
4. 目的： 
    - 保持 Repository 結構清晰
    - 降低維運與認知成本

---

##### 九、分支命名規範

9.1 基本格式

<div class="sticky top-[calc(--spacing(9)+var(--header-height))] @w-xl/main:top-9" id="bkmrk--21"><div class="absolute end-0 bottom-0 flex h-9 items-center pe-2"><div class="bg-token-bg-elevated-secondary text-token-text-secondary flex items-center gap-4 rounded-sm px-2 font-sans text-xs">  
</div></div></div><div class="overflow-y-auto p-4" dir="ltr" id="bkmrk-%5B%E5%9F%BA%E5%BA%95%E5%88%86%E6%94%AF%5D%2F%5B%E8%AD%B0%E9%A1%8C%E7%B7%A8%E8%99%9F%5D-%5B%E6%8F%8F%E8%BF%B0%5D">`<span class="hljs-selector-attr">[基底分支]</span>/<span class="hljs-selector-attr">[議題編號]</span>-<span class="hljs-selector-attr">[描述]</span>`</div>---

9.2 開發主分支（單一負責）

<div class="sticky top-[calc(--spacing(9)+var(--header-height))] @w-xl/main:top-9" id="bkmrk--23"><div class="absolute end-0 bottom-0 flex h-9 items-center pe-2"><div class="bg-token-bg-elevated-secondary text-token-text-secondary flex items-center gap-4 rounded-sm px-2 font-sans text-xs">  
</div></div></div><div class="overflow-y-auto p-4" dir="ltr" id="bkmrk-dev%2F56-kcgsso">`dev/56-KcgSso`</div>---

9.3 多人協作次分支

- **人員維度**<div class="sticky top-[calc(--spacing(9)+var(--header-height))] @w-xl/main:top-9"><div class="absolute end-0 bottom-0 flex h-9 items-center pe-2"><div class="bg-token-bg-elevated-secondary text-token-text-secondary flex items-center gap-4 rounded-sm px-2 font-sans text-xs">  
    </div></div></div><div class="overflow-y-auto p-4" dir="ltr">`dev/56-KcgSso/wilson`</div>
- **功能維度**<div class="sticky top-[calc(--spacing(9)+var(--header-height))] @w-xl/main:top-9"><div class="absolute end-0 bottom-0 flex h-9 items-center pe-2"><div class="bg-token-bg-elevated-secondary text-token-text-secondary flex items-center gap-4 rounded-sm px-2 font-sans text-xs">  
    </div></div></div><div class="overflow-y-auto p-4" dir="ltr">`dev<span class="hljs-regexp">/56-KcgSso/</span><span class="hljs-type">Login</span>`</div>

---

9.4 緊急修復分支

<div class="sticky top-[calc(--spacing(9)+var(--header-height))] @w-xl/main:top-9" id="bkmrk--26"><div class="absolute end-0 bottom-0 flex h-9 items-center pe-2"><div class="bg-token-bg-elevated-secondary text-token-text-secondary flex items-center gap-4 rounded-sm px-2 font-sans text-xs">  
</div></div></div><div class="overflow-y-auto p-4" dir="ltr" id="bkmrk-fix%2Fcs-2024001-fix%2F9-1">`<span class="hljs-built_in">fix</span>/CS<span class="hljs-number">-2024001</span><span class="hljs-built_in">fix</span>/<span class="hljs-number">99</span>-Hotfix`</div>---

##### 十、責任與違規處理

1. 本制度為 **DTD 技術強制性制度**
2. 違反規範者： 
    - GitLab 管理者有權退回 MR
    - 情節重大者，提報 PMO / GM 評估處置
3. 本制度將作為： 
    - 專案稽核依據
    - 技術交接與教育訓練基準