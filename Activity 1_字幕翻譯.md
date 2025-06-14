以下是你的 PeopleSoft 文章摘要，每段以 3 到 5 條列式說明：

### **PeopleSoft 應用程式開發過程回顧**
- 本活動將回顧 PeopleSoft 應用程式開發的八個步驟，並以 Training Tasks 應用程式為例進行說明。
- 在回顧過程中，將探討 PeopleCode 如何增強並完善應用程式。
- 目標是了解開發流程的結構化方法，並掌握核心步驟。

### **應用程式開發過程詳細步驟**
- PeopleSoft 應用程式開發流程包括八個步驟：規劃應用程式、定義欄位、定義記錄、建立表格、定義頁面、定義元件、註冊元件、測試應用程式。
- 每個步驟將有詳細說明，以確保完整理解與應用。
- 開發流程強調系統化設計，以確保應用程式的功能性與可擴展性。

### **步驟 1：規劃應用程式**
- 此步驟是整個開發流程中最具挑戰性的部分，涉及應用程式架構與設計。
- 需要使用 PeopleSoft Application Designer，以兩層模式啟動應用程式設計工具。
- 設定資料庫連線（Oracle，T1B85701），並確認使用者 ID 及密碼（PTCODE）。
- 進一步優化工作流程，例如將應用程式設計工具捷徑設置於桌面。
- 調整 Configuration Manager 設定，確保登入時系統預設使用 PTCODE。

### **介面與設計最佳化**
- 可透過 ALT-2 快速關閉 Property Window，以擴大工作區域。
- 亦可透過 Tools > Options > General tab 取消「Enable Property Window」選項，使設定持久生效。
- 開啟 **PSU_TASKS** 專案，以方便存取元件、欄位、頁面及記錄等物件。
- 設定 **Insert Definition into Project Group** 選項，使物件修改後能自動更新至專案。
- 啟用 **Reload last project at startup**，確保每次啟動 Application Designer 時專案能自動載入。




### **專案概述與變更**
- PSU_TASKS 專案已建立，現需對其進行修改以符合新需求。
- Oracle University 需開發一套應用程式來追蹤課程開發項目，每個項目包含多個任務。
- 需記錄資源分配情況，包括日期、工作時數等，以便於獨立追蹤任務與資源。

### **PeopleCode 應用**
- 除了使用現有的 Records、Components、Pages，還需撰寫 PeopleCode 來完成特定業務邏輯。
- PeopleCode 可用於驗證輸入、控制元件行為以及動態處理數據。
- 增強系統的靈活性，使其更適應不同需求場景。

### **欄位定義與特性**
- 在專案工作區展開 Field 資料夾，雙擊開啟 **TASK_STATUS** 欄位以查看其屬性。
- 欄位特性為全域性，變更欄位屬性後，所有引用該欄位的記錄將同步更新。
- TASK_STATUS 為單字元欄位（最大長度 1），所有數據均以大寫格式存儲。
- 可透過 Translate Values 定義欄位有效值，如 **A（Assigned）、C（Completed）、S（Started）、U（Unassigned）**。

### **屬性設定與介面優化**
- 可透過 Toolbar 的 **Properties** 按鈕查看欄位屬性與文件化資訊。
- 進入 **Translate Values** 標籤，可查閱欄位對應的有效數據與 PeopleSoft 預設值。
- 欄位驗證至 **PS Item 表**，其值通常擁有 **1901/01/01** 的生效日期，代表其為系統預設可用的值。




 

### **記錄定義與屬性**
- **PSU_TASK_RSRC** 記錄定義預設顯示為 Field Display，展示各欄位的屬性與定義。
- 記錄定義作為 SQL 表格的藍圖，欄位將成為表格的列。
- 在 Use Display 模式下，可設定鍵值欄位，用於識別唯一的資料行。
- **TASK** 和 **RESOURCE_NAME** 為主要鍵值，採用遞增排序。
- 可額外設定搜尋鍵、替代鍵或提示表查詢，但此記錄目前未設定。

### **欄位屬性與預設值**
- **RESOURCE_NAME** 欄位為鍵值，預設值為 **PSU_INSTR_NM_VW**，顯示來自 SQL 視圖的資料。
- 該視圖提供預設數據，定義如何從其他表中擷取資源名稱。
- **INSTRUCTOR** 欄位並非鍵值，使用 **Prompt Table Edit** 方式連結 **PSU_INSTR** 表。
- 可透過 Prompt Table 選擇指導者，或直接輸入資源名稱（若非指導者）。
- **INSTRUCTOR** 欄位非必填，但通常會與 RESOURCE_NAME 關聯。

### **記錄用途與應用場景**
- **PSU_TASK_RSRC** 用於管理任務資源，追蹤工作項目的時間與參與人員。
- 任務可包括技術開發、教學內容撰寫、或 IT 系統維護等。
- 資源可為不同職能角色，如指導者、DBA、技術編寫人員等。
- 系統允許獨立管理任務與資源，使應用更具靈活性。
 





### **PSU_TASK_EFFORT 記錄定義**
- **TASK_EFFORT** 為 **PSU_TASK_RSRC** 的子記錄，鍵值欄位包括 **TASK、RESOURCE_NAME、EFFORT_DATE**。
- 確保與父記錄的鍵值一致，並額外添加 **EFFORT_DATE** 作為獨立鍵值。
- 用於追蹤每個資源在特定任務上的工時與工作日期。
- 適用於管理 PeopleSoft Fluid User Interface 開發過程的資源投入情況。

### **SQL 表格建置**
- 建立資料庫表格為開發過程中最容易被忽略的步驟。
- 應用程式開發時，通常需創建新的表格來存儲數據。
- 需使用 **Build > Current Definition** 來建立表格，可選擇直接執行 SQL 或產生腳本。
- 若表格已存在，直接重建可能會導致資料遺失，因此需謹慎操作。

### **PSU_TASK_RESOURCES 頁面定義**
- 頁面包含三個層級：**Level 0（PSU_TASKS）、Level 1（PSU_TASK_RSRC）、Level 2（PSU_TASK_EFFORT）**。
- 允許 **Deferred Processing**，但仍需在組件層級進行啟用。
- 如果元件設為 **Interactive Mode**，則即使頁面允許 Deferred Processing，仍會以互動模式運作。
- 若元件設為 **Deferred Mode**，則處理方式將由頁面與欄位設定決定。

### **Deferred Processing 的層級影響**
- **Deferred Processing** 先由 **元件** 決定，再由 **頁面** 確定，最後才影響個別欄位。
- 若元件設為互動模式，則所有欄位均以即時方式處理。
- 若元件允許 Deferred Processing，則頁面可啟用此功能，進而影響頁面內的各個欄位。



### **定義元件 (Component)**
- **TASK_RESOURCES** 元件屬性可在 **Definition** 標籤啟動時存取，包含各頁面的標籤名稱。
- **General** 標籤可用於設置文件化資訊與元件基本描述。
- **Use** 標籤指定搜尋記錄，決定元件的搜尋頁面如何建立與行為。
- **Internet** 標籤包含 **Processing Mode** 設定，可選擇 **Interactive** 或 **Deferred** 模式。

### **處理模式 (Processing Mode)**
- 若元件設為 **Deferred Mode**，則將處理延遲至頁面層級，再進一步遞延至頁面控制項。
- 若元件設為 **Interactive Mode**，所有處理將即時執行，不受頁面設定影響。
- Deferred Processing 允許系統在提交時統一處理資料，提高效能。

### **結構與層級**
- 在 **Structure** 標籤可查看層級架構：
  - 搜尋記錄來自 **PSU_TASKS** 表。
  - **Level 0** 資料來自 **PSU_TASKS** 表。
  - **Level 1** Scroll Area 來自 **PSU_TASK_RSRC** 表。
  - **Level 2** 來自 **PSU_TASK_EFFORT** 表。
- 各層級負責不同的數據管理，確保應用程式的結構清晰。



### **元件註冊 (Component Registration)**
- **Component Registration Wizard** 用於將元件附加至選單定義、分配安全性存取，並建立導覽連結。
- 本課程中的所有元件已完成註冊，無需使用此向導。
- 註冊元件後，該元件將出現在 **Application Designer** 的選單中，方便存取與管理。
- 註冊過程同時將元件添加至 **Portal Registry** 內的現有資料夾，以供 PIA 導覽使用。
- 給予元件 **Permission List** 權限，確保使用者能夠存取該元件。

### **應用程式測試**
- 透過 **T1B85701** 桌面圖示啟動 Web 瀏覽器，並登入 **PeopleSoft** 系統 (PTCODE) 進行測試。
- 從 **Navigator** 選擇 **Setup Training > Training Tasks > Task Table** 以存取 **Tasks** 頁面。
- 系統當前已建立五個任務，包括 **PeopleTools Training Guide**、**Live Webcast** 等。

### **建立與管理新任務**
- 在 **Task Table** 頁面可選擇 **Add** 以新增新任務，例如「PeopleSoft Fluid User Guide」。
- 設置 **短描述**（如 FLUID），並估算 **總工作時數**（例如 1000 小時）。
- 設置 **開始日期**（預設為今日）與 **預計完成日期**，目前尚未分配資源。
- 儲存後可檢視新建立的任務，以進一步分配資源與追蹤進度。




### **檢視現有任務**
- 透過 **F5** 進入搜尋頁面，可查閱已建立的任務，如 **Task 1: PeopleTools 1 Training Guide**。
- 該任務的 **總工時** 為 1,200 小時，其中 **已投入** 480 小時，**完成日期** 為 2002/06/23。
- 任務已標記為 **完成狀態**，可透過 **Task Table** 查閱詳細資訊。

### **存取任務資源與進度**
- 透過 **Navigator > Task Resources and Efforts** 進入 **Task Resources** 頁面。
- 頁面加載時預設載入 **Task 1**，顯示已參與的四位人員：**Ed、Jim Guss、Joe Yang、Scott Sanchez**。
- 各資源的可用性不同，例如 **Ed 50% 可用，且已完成任務**。

### **分配新資源至任務**
- 可在 **Task Resources** 頁面手動分配新資源，如指導者或其他角色。
- 設定 **可用比例**（如 25%）並儲存，但該資源尚未投入工時。
- 建議在 **Task Table** 頁面標記任務狀態，或透過 **PeopleCode** 自動更新關聯頁面的狀態。
- 可能需要撰寫 **PeopleCode** 來自動變更 **Task Status** 欄位，確保系統內資料同步。



### **同步工時與收費資料**
- 需確保所有資源投入的總時數與 **Task Table** 內的 **Charge Back Hours** 保持一致。
- 建議透過 **PeopleCode** 自動同步已分配任務的工時，避免數據不一致問題。
- 須驗證累計工時與個別資源所記錄的努力日期與時數，確保準確性。

### **新增任務與資源**
- 可在 **Task Resources and Efforts** 頁面新增資源並分配努力日期與時數。
- 設定不同資源的可用比例（例如 25% 或 10%），並新增多筆投入時數。
- 存儲資料後，應驗證 **Task Table** 是否自動更新工時，若未更新需透過 **PeopleCode** 實現同步。

### **PeopleCode 檢核機制**
- 需避免輸入異常數據，如：
  - **結束日期早於開始日期**
  - **已投入工時超過分配總時數**
  - **未指派資源但標記為已完成**
- 可透過 **PeopleCode** 設置驗證邏輯，以確保系統完整性並防止錯誤輸入。

