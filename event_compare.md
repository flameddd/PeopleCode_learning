
 
|   | **SearchInit** | **SearchSave** |  |
|---|---|---|---|
| 觸發時機 | 1. User開啟「搜尋/新增」對話框時執行 | User在搜尋頁「按下 **Search / Add**」後、元件真正被開啟之前觸發。 | 一前一後：SearchInit 用來**布置搜尋頁**，SearchSave 用來**判斷是否允許進入**。 |
| 可存取物件 | 只能存取 **Search Record** 中的欄位<br>無法存取 Component Buffer，因為尚未建構。 | 同左；仍僅有搜尋頁欄位可用。 | 兩者都發生於「Component 之外」，所以不能用 `GetLevel0()` 等。 |
| 主要用途 | • 預帶預設值 (`FIELD.Value = ..`)。<br>• 控制唯讀/隱藏。<br>• 用 `SetSearchDialogBehavior()` 自動跳過搜尋頁。 | • 驗證搜尋 Key是否存在 / 是否為合法組合。<br>• 若無權限，可 `Error()` 阻擋。 | SearchSave 是防線：只有它可以真正終止進入 Component |
| 常見問題 | • 在此做 heavy task 影響搜尋頁載入速度 | • 忘了對重複鍵或權限驗證 → User可進入但後續 SaveEdit 才報錯 |  |




| | **FieldEdit** | **FieldChange** |
| --- | --- | --- |
| 順序 | FieldEdit → FieldChange → (SaveEdit, SavePreChange, …) | 位於 FieldEdit 之後；若前者失敗則不會執行。 |
| 觸發時機 |  User 「離開欄位」時立即執行。若頁面設為 *Deferred Processing*，則在 **save** 時才批次執行。 | 只有當 **FieldEdit 完成且未拋出 Error** 後才觸發。同樣受 *Deferred Processing* 影響，可能延後到 save 階段。 |
| 主要用途 | 驗證輸入值，不符合時以 `Error()` / `Warning()` 阻止後續處理。不能修改其他欄位 | 依欄位變動「衍生」或「影響」其他欄位／邏輯，例如重新計算金額、帶出預設值、啟用/停用控制項。 |
| | ‑ 欄位長度、格式、範圍檢查  <br>- 業務規則（例：不得超過預算） | ‑ 依輸入自動計算 (Qty × Rate = Amount)  <br>- 修改頁面狀態：`SetCursorPos()`, `Enable()`/`Disable()`  <br>- 讀取其他記錄以帶值 |
| 對儲存流程的影響 | `Error()` 會中斷 User 動作。若發生 Error，**FieldChange 不會執行**。 | 就算 `Warning()` 顯示警示， User 仍可繼續操作並儲存；`Error()` 應盡量避免放在此事件，以免難以追蹤。 |
| 常見問題 | 在 FieldEdit 進行大量 IO，導致效能問題 | • 在 FieldChange 做驗證卻沒擋住錯誤資料，導致不符合的資料被寫入。<br>• 忘記考量 Deferred Processing，導致欄位未即時更新。 |




|  | 觸發先後 | 主要用途 |
| --- | --- |  --- |
| **PreBuild** | 1 第一個被呼叫 | ‑ 動態決定哪個 PageSet 預設顯示<br>- 依登入者權限轉向 | 
| **RowSelect** | 2 針對每一筆即將載入的 Row 呼叫 |   ‑ 篩選資料列 (`RowSelect = False`)<br>- 只讓有效、合權限資料進入頁面 | 
| **FieldDefault** | 3 於每列插入 Buffer 時、對 **每個欄位** 觸發 |   ‑ 填入系統／業務預設值<br>- 帶流水號、預設日期 |
| **FieldFormula** | 4 跟在 FieldDefault 後、同樣對「每欄」跑 |   ‑ 派生計算值<br>- FUNCLIB 共用副程式集中放這裡 |
| **RowInit** | 5 每筆 Row 完成後呼叫一次 |  ‑ Enable/Hide 欄位<br>- 初始化 Grid 樣式、按鈕 | 
| **PostBuild** | 6 Component 全部 Row 建完後 |  ‑ 控制 Tab order、動態隱藏 Page、修改標題<br>- 設定頁面級安全性 | 
| **Activate** | 7 **每次切入該 Page** 都會跑 |  ‑ 頁面進入時最後 UI 調整：Grid 方法、Dynamic Prompt<br>- 最終安全檢查（隱頁、Disable） | 
 

| | **RowInsert** | **RowDelete** |
| --- | --- | --- |
| 觸發時機 | • User 點「+」<br>• PeopleCode 叫用 `InsertRow()` / `Scroll.InsertRow()` | • User 點「-」<br>• PeopleCode 叫用 `DeleteRow()` / `Scroll.DeleteRow()` |
| 執行順序 (單筆資料流程) | 1. **RowInsert**<br>2. **RowInit**（對新列）<br>3. 使用者繼續輸入 → FieldEdit → FieldChange… | 1. **RowDelete**<br>2. **RowInit**（對刪除後下一列，因畫面更新 |
| 主要用途 | • 預設欄位值 (`RECORD.FIELD.Value = ...`)<br>• 複製上一列資料作快速新增<br>• 動態控制新增行數上限（超過則 `Error()`） | • 驗證是否允許刪除 <br>• 累計已刪除列的資料量，稍後更新彙總<br>• 觸發業務邏輯 |
| | 設定預設值、自動編號、調整有效日期 | 重新計算資料(訂單總額)、調整行號、防止刪除 |
| 阻止動作的方法 | `Error()`：**立即取消新增** | `Error()`：**取消刪除**，列保留 |
| 與 DB 互動 | 只在 **Component Buffer** 加新 Row，尚未寫入 DB。實際 INSERT 發生在 `SavePostChange` | 只將 Row 標記為 *Delete Pending*，尚未刪表。真正 DELETE 亦在 `SavePostChange` |
| 注意事項 | • **RowInit 會緊接著執行**，避免重複預設邏輯。<br>• 若在 RowInsert 做大量 SQL，效能易受影響。 | • 刪除前需檢查外鍵：可用 `Select()` 或 `SqlExec()` 判斷子表。<br>• 刪除後若要即時更新頁面彙總，須在 RowDelete 同步計算。 |
| 需注意常見問題 | • 在 RowInsert 用 `SaveEdit` 等語法阻止新增 → 邏輯錯位。<br>• 忽略 Deferred Processing，導致預設值未即時顯示。 | • 在 RowDelete 直接呼叫 `CommitWork()` → 破壞 Component Processor 流程。<br>• 刪關鍵資料但沒同步移除暫存變數，導致 SaveEdit 失敗。 |




| 面向 | **SaveEdit** | **SavePreChange** | **Workflow** | **SavePostChange** |
|---|---|---|---|---|
| 觸發順序 | 1（FieldEdit/RowEdit 之後） | 2（所有驗證通過後，真正寫 DB 前一刻） | 3（SavePreChange 結束緊接著） | 4（資料已寫入 DB 之後） |
| 執行時機點 | 準備寫 DB 前，**最後整體驗證** | 在 Buffer → DB 前，仍可改 Component Buffer | 在同一交易內，資料尚未 commit | 資料已插/改/刪成功 |
| 是否可 **阻擋 save** | 可用 `Error()/Warning()` | 可用 `Error()`，但不建議 | 不應該 | 不應該 |
| 主要用途 | ‑ 跨欄位/跨 Row 的資料驗證<br>- 最後的業務邏輯審核 | ‑ 產生系統欄位：流水號、時間戳、補資料 <br>- 同步欄位一致性 | ‑ 設定 `WORKLIST_REQ`, `WF_EVENT` 等欄位<br>- 送 Worklist / Email | ‑ 更新 table<br>- 呼叫 CI、REST、Pub/Sub<br>- 寫 audit/log |
| 與 **交易/Commit** 關係 | 尚未開始 DB 更新 | 尚未開始 DB 更新 | 尚未 Commit | 尚未 Commit，但 DB 內已有資料 |
| 需注意常見問題 | ‑ 大量 SQL 影響效能<br>- 忘記重新驗證批次匯入資料 | ‑ 在此拋 Error → 使用者見到怪訊息<br>- 變更不在 Buffer 的表，結果被滾回 | ‑ 在此查表卻看不到「自己剛寫」的資料（尚未落地） | ‑ 用 `Error()` 只會回 Rollback 給整批，使用者難理解 |



|  | **Add Mode** (`%Mode = "A"`) | **Update**（`%Mode = "U"` / `"L"` / `"C"`） |  |
|---|---|---|---|
| 入口 | Search Page 點 **Add** | Search Page 點 **Search** | 新增一筆 vs. 維護既有資料 |
| Component Buffer 載入 | 僅載入關鍵欄位 (`Search Keys`) | 按有效日期規則載入現有資料 | Buffer 乾淨，Update 則已含資料 |
| Search Keys | **可輸入/編輯** ➜ 儲存後成為 PK | **唯讀**；決定讀哪筆資料 | 只有 Add 允許新增 PK |
| 有效日期 | 系統插入 `EFFDT`，通常 = `%Date` | 依 Component |  |
| 主要 Event 差異 | • SearchInit → SearchSave<br>• **FieldDefault → FieldFormula → RowInit**<br>（Add 專屬建構流程） | • PreBuild → RowSelect → RowInit<br>（Update 先挑列，再跑初始化） |  |
| 常見驗證位置 | `SearchSave`：重複Keu、權限<br>`SaveEdit`：跨欄位驗證 | `FieldEdit` / `SaveEdit`：欄位驗證、業務邏輯 | |
| 預設值處理 | `FieldDefault` 會大量觸發；常用於帶流水號、系統預設 | 預設值通常已存在；`FieldDefault` 很少被執行 | |
| 主要用途 | 新增資料 | 修改資料 |  |


|  | **Deferred Processing** | **Interactive Mode** |  |
|---|---|---|---|
| 事件觸發時點 | FieldEdit／FieldChange 等「欄位修改事件」被延後，直到執行某些動作：<br>• 點儲存、按按鈕等 | User 離開欄位 (Click elsewhere) 時即刻送往伺服器執行 | 延後 vs 即時  |
| Server trip 次數 | 極少；一次動作可能批次送出多欄驗證 | 多；每次離開欄位就往返一次 |  |
| 使用者體感 | 連續輸入、不被驗證訊息打斷 | 輸入即時獲得錯誤／Derived Values | 考量立即性 |
| 主要用途 | 輸入大量資料、表單長 | 關鍵欄位需即刻驗證、計算或動態顯示其他欄位 | 可混用：整體 Deferred，少數 Interactive |
| 預設 | Component 預設為 Deferred | 需在 Component／Page／Field 取消「Allow Deferred Processing」 | |
| 覆寫規則 | Component 設 Deferred 時，可在 Page 或 Field 個別改成 Interactive | Component 設 Interactive 時，下層無法再改回 Deferred |  |
| 需注意常見問題 | 忘了 Deferred，User 離開欄位卻沒看到 Derived Values；以為失效 | 在 Interactive 中寫大量 SQL，User 每離開欄位就 Lag | |




|  | **Local 變數 (`Local &`)** | **Component 變數 (`Component &`)** | **Global 變數 (`Global &`)** |
| --- | --- | --- | --- |
| 存取範圍 | 僅限當前事件或function內 | 可在相同component內的所有事件間存取 | 可在所有component、所有事件間存取 |
| 生命週期 | 只在事件執行期間有效 | component開啟後到關閉前都有效 | 保留至使用者登出或 Session 終止 |
| 主要用途 | 暫時性計算資料 | component內共享的資訊 | Session 內的共享的資訊 |
| 跨 event 存取 | 不能跨，event 結束變數就消失 | 可以跨event，但僅限於 component 內 | 可跨所有 event |
| 跨 component 存取 | 不能 | 不能 | 可以 |
