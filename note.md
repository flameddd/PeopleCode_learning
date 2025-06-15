## 1. PeopleCode Course Overview

介紹課程大綱

--------

## 2. PeopleCode Technology Overview


### **Component Processor Flow**
- **PeopleCode 可用於 Component, Page, Record Field 及 Menu**
- **Component Processor Flow** 控制 **資料載入、Buffer處理** 及 **頁面顯示**
- 用 **PeopleCode** 確保 User 輸入符合業務邏輯

![alt text](2_event_01.png)  
![alt text](2_event_02.png)   

    

--------

## 3. Using PeopleCode Development Tools
- Using PeopleCode Development Tools
- Locating PeopleCode Programs
- Using the PeopleCode Debugger
- Describing Additional Development Tools
- Activity 1: Reviewing the PeopleSoft Application Development Process
- Activity 2: Using the PeopleCode Editor
- Activity 3: Debugging PeopleCode Programs

3.1 也是在介紹 PeopleCode 能做到什麼，沒什麼好講解的  

3.2 Locating PeopleCode Programs 就值得講了  
開始講 localtion 了


### **PeopleCode 的三大考量**
1. **WHERE (程式位置)**
   - **Component 人工影響範圍較小**，僅影響單一元件，適合局部應用。
   - **Record Field 影響範圍較廣**，影響 **多個元件**，適合全系統規則。

2. **WHEN (事件觸發時機)**
   - **事件是 PeopleSoft 預設的中斷點**
   - 常見事件: 
     - **RowInit**(資料初始化)
     - **FieldChange**(欄位變更)
     - **SavePreChange / SavePostChange**(存檔前後處理)
3. **WHAT (程式語法)** 
    - 業務邏輯

-----

![alt text](3.2_event_01.png)  
![alt text](3.2_event_02.png)  
![alt text](3.2_event_03.png)  
![alt text](3.2_event_04.png)  
![alt text](3.2_event_05.png)  
![alt text](3.2_event_06.png)  
![alt text](3.2_event_07.png)  
![alt text](3.2_event_08.png)  
![alt text](3.2_event_09.png)  
![alt text](3.2_event_10.png)  
![alt text](3.2_event_11.png)  
![alt text](3.2_event_12.png)  
![alt text](3.2_event_13.png)  
![alt text](3.2_event_14.png)  
![alt text](3.2_event_15.png)  
![alt text](<Activity 2_06.png>)   
![alt text](<Activity 3_15.png>)  
![alt text](<Activity 3_16.png>)   
![alt text](3.2_event_16.png)  

3.3 Using the PeopleCode Debugger

Debug 的方法:
1. **MessageBox & WinMessage**  
- `MessageBox(style, title, message_set, message_num, default_txt [, paramlist])`: 可顯示訊息，適合快速檢查變數值與執行流程。
- `WinMessage(message [, style] [, title])`: 類似 `MessageBox`，但更簡單，適合臨時測試。

2. **PeopleCode Debugger**  
- 可設定 **斷點(Breakpoints)**，逐步執行程式碼，檢視變數值與緩衝區內容。
- 啟用 ![alt text](<Screenshot 2025-05-27 at 23.00.17_small.png>)  
- 開啟後，有更多的東西可以開啟  
![alt text](<Screenshot 2025-05-27 at 23.02.49.png>)   
![alt text](<Activity 3_4.png>)    
- 離開 ![alt text](<Activity 3_17.png>)   


3. Trace log
- ![](<Trace PeopleCode Page_04.png>)
- ![alt text](<Trace PeopleCode Page_06.png>)


3.5 Activity 1: Reviewing the PeopleSoft Application Development Process


**Deferred Mode的影響**
- 設定是一層一層影響的
  - So first it checks the component, then the page, and then the fields.
- 若 Component 設為 Interactive Mode(互動模式)，則 Page 和 Fields 的 Deferred 設定無效
- 若 Component 設為 Deferred Mode(延遲模式)，則 Page 的 Deferred 設定生效，再依序影響各 Fields

  ![alt text](page_defered_processing_01.png)  
  ![alt text](page_defered_processing_02.png)  


Interactive Mode(互動模式)
- 即時 submit 變更: User 在 Page 上輸入或修改資料後，每次點 save 、切換欄位或觸發事件時，系統會立即執行資料驗證與 submit
- 適合即時回應: 用於需要立即回饋或資料必須馬上被處理的情境，例如即時計算薪資或費用
- 可能影響效能: 由於每次操作都會觸發處理，可能導致伺服器頻繁運算，影響系統效能。

Deferred Mode(延遲模式)
- 延遲處理: User 的輸入不會立即觸發 submit ，而是等到點選 submit 或執行某個特定動作時才一併處理。
- 提升效能: 適用於批次作業或大量資料處理，減少即時計算對系統的影響。
- 更適合長表單輸入: 例如需要填寫多個欄位後才進行驗證的表單，避免每次輸入都觸發系統運算





3.6 Activity 2: Using the PeopleCode Editor

跟上面 3.2 差不多的東西走過一遍  

可以從左邊把東西往 Editor 拉  
![alt text](<Activity 2_10.png>)  

PeopleCode 自動儲存機制
- PeopleCode 編輯器在每次輸入時自動備份，存放於 TMP 目錄。
- TMP 目錄通常位於 Windows 系統的 TMP 路徑，而非 C:\Temp。
- 可透過 Windows 指令 `set` 來檢視 TMP 目錄的實際位置。
- 自動儲存檔案名稱格式為 PPCMMDDYY_HHMMSS，其中 MMDDYY 為日期，HHMMSS 為建立時間
- 儲存 PeopleCode 後，備份檔案將被刪除，可嘗試輸入新內容並再次檢視。


3.7 Activity 3: Debugging PeopleCode Programs


--------
## 4.1 Understanding the Component Processor and PeopleCode Events

- 理解 Component Processor flow  
- identify PeopleCode events, describe
  - search events
  - component build and page display events
  - field action events
  - row action events
  - save action events
  - add mode processing

### **追蹤 Component Processor 流程**
- 在撰寫 PeopleCode 程式前，需決定程式執行的時機點(例如 FieldEdit、FieldChange、SavePreChange 等)。
- 決定 PeopleCode 的放置位置(Component 層級、Record 層級、Page 層級等)。


### **搜尋與 Component Buffer**
- 使用 Search Record 建立搜尋頁面，依據欄位屬性設定搜尋關鍵字、替代搜尋鍵及結果列表框。
- 當使用者執行搜尋，系統根據 Search Key 產生 SQL `SELECT` 語句並載入對應的資料。
- Component Processor 迴圈處理資料庫中的每一行資料並載入 Component Buffer。

當我們用 Search Record 搜尋後，

### **Component Buffer 建構過程**
- 檢查是否處於 Add Mode，若非 Add Mode，則執行 SQL `SELECT` 並載入對應資料。
- 逐步載入 Component Buffer，檢查是否有更多資料列需要讀取並存入緩衝區。
- Apply default value to display Page

### **Component 層級資料載入**
- 載入 Level 0 ~ 3 資料
  - **確保所有資料都載入至 Buffer**，並在每個層級反覆執行資料處理。
- **Row 是 Component Buffer 的單位**: PeopleSoft 使用 **Row Set** 來管理多筆 Row 資料的載入與存儲。
  - **由 Record 組成**: 每個 Row 對應於一個 **Record**，而 Record 內含多個欄位 (Fields)。


### **套用 Record 預設值**
- **應用記錄的預設值**: 根據 Record Field 設定，將預設值套用至無資料的欄位。
- **處理系統預設值**: 若 Record Field 無預設值，則套用系統預設，例如文字欄位設為空白，數字欄位設為 0。
- **顯示頁面並等待使用者操作**: 所有資料完成載入後，系統顯示頁面並準備接受使用者互動。

 
### Field Change Action
- **使用者修改欄位值**，系統執行標準系統驗證(如 Prompt Table Edit, Translate Table, Yes/No Edit)。
- **如果驗證失敗**，則顯示錯誤訊息並停留在頁面上，等待使用者修正輸入。
- **如果驗證通過**，則接受變更並重新套用預設值，頁面準備下一步使用者操作。

### **Row Action**
- **Row Insert**: 
  - 點「+」按鈕新增一行資料。
  - 系統套用記錄預設值並顯示新行，等待使用者輸入資料。

- **Row Delete**: 
  - 點「-」按鈕移除特定行
  - **如果系統允許刪除**，則移除該行並重新載入頁面
  - **如果刪除受限**，則顯示錯誤訊息，拒絕刪除




開啟 Page 時，Component Processor 會把資料 load 進來，然後等待 User 動作  

![alt text](<Component Processor_01.png>)  
![alt text](<Component Processor_02.png>)  
![alt text](<Component Processor_03.png>)  
![alt text](<Component Processor_04.png>)  
![alt text](<Component Processor_05.png>)  
![alt text](<Component Processor_06.png>)  
![alt text](<Component Processor_07.png>)  

 
--------------   

## 4.2 Identifying PeopleCode Events

### ** Event 的位置**
- **Component**
  - **Component**
  - **Component Record**
  - **Component Record Field**
- **Menus**
- **Pages**
- **Record Fields** (記錄欄位)


### **PeopleCode Event 類型**
- **SearchAction Events**: `SearchInit`、`SearchSave`，用於處理搜尋頁面
- **Component 建構與 Page dispaly (Component Build & Page Display Events)**: 
  - `RowSelect`, `PreBuild`, `FieldDefault`, `FieldFormula`, `RowInit`, `PostBuild`, `Activate`
- **FieldAction Events**: 
  - `FieldEdit`, `FieldChange`
- **RowAction Events**: 
  - `RowInsert`, `RowDelete`
- **SaveAction Events**: 
  - `SaveEdit`, `SavePreChange`, `Workflow`, `SavePostChange`

### **非 Component Processor 事件**

### **SearchInit event**
- 當使用者透過 **Navigator** 或 **Content Reference** 選擇某個 **Component**，該元件會被載入。
- **SearchInit 事件** 會清除 Component Buffer，建立搜尋頁面並準備載入資料。
- **SearchSave 事件** 用於檢查搜尋結果並驗證輸入。

### **SearchInit 事件用途**
- **執行時機**: 在搜尋頁面顯示之前執行
- **設預設值**: 可在進入搜尋頁面前，設定某些欄位的預設值，例如設為目前登入使用者的 ID
  - 可利用 **系統變數** (`%UserID`, `%EMPLID`, `%Date` 等) 來設定值
- **控制欄位狀態**: 
  - **Disable 欄位**: 使使用者無法修改。
  - **Hide 欄位**: 可隱藏特定欄位，使其不出現在搜尋頁面。

### **SearchInit 用於安全性與行為控制**
- **控制安全性存取**: 
  - 預設情況下，若 `EMPL_ID` 為鍵值且與登入使用者相符，系統不允許更改。
  - 可透過 `Allow EMPL ID Change = True` 覆寫預設行為，允許修改該欄位。
- **略過搜尋頁面**: 
  - 設定 `SearchDialogBehavior = 0`，可直接跳過搜尋頁面，進入 Component。
  - 適用於當前已知 search key 的情境

### **SearchInit 限制**
- **某些 PeopleCode 函數無法在 SearchInit 中使用**: 
  - `DoModal`, `Transfer`, `TransferExact`, `TransferNode`, `TransferPortal` **等函數不可用**。
- **SearchInit 的變數不會傳遞至後續頁面。Search Page 有獨立的 Buffer**


### **SearchSave 事件的應用**
- **執行時機**: 在使用者點擊 `Search` 或 `Add` 按鈕後執行。
- **驗證搜尋輸入值**: 
  - 可使用 `SearchSave` 限制使用者的搜尋條件，例如管理者只能搜尋自己部門的員工。
  - 可透過 `Error` 或 `Warning` 函數 **阻止使用者繼續操作**，並返回搜尋頁面。


### **SearchInit 與 SearchSave 的區別**
| 事件 | 觸發時機 | 主要用途 | 是否可用錯誤處理 |
|-------------|----------------------------------|--------------------------------------|----------------|
| `SearchInit` | 搜尋頁面顯示前 | 設定預設值、隱藏/禁用欄位、跳過搜尋頁面 | ❌ 不可使用 `Error` 或 `Warning` |
| `SearchSave` | 使用者點擊 `Search` 或 `Add` 按鈕後 | 驗證搜尋值、限制使用者搜尋條件 | ✅ 可使用 `Error` 或 `Warning` |
 



![alt text](<4.2 Identifying PeopleCode Events_01.png>)  
![alt text](<4.2 Identifying PeopleCode Events_02.png>)  
![alt text](<4.2 Identifying PeopleCode Events_03.png>)  
![alt text](<4.2 Identifying PeopleCode Events_04.png>)  
![alt text](<4.2 Identifying PeopleCode Events_06.png>)  
![alt text](<4.2 Identifying PeopleCode Events_07.png>)  
![alt text](<4.2 Identifying PeopleCode Events_08.png>)  
![alt text](<4.2 Identifying PeopleCode Events_09.png>)  
![alt text](<4.2 Identifying PeopleCode Events_10.png>)  
![alt text](<4.2 Identifying PeopleCode Events_11.png>)  
![alt text](<4.2 Identifying PeopleCode Events_12.png>)  
![alt text](<4.2 Identifying PeopleCode Events_13.png>)  
![alt text](<4.2 Identifying PeopleCode Events_14.png>)  


-------

## 4.3 Describing Component Build and Page Display Events

**`RowSelect`**: 決定 **哪些行資料將載入至 Component Buffer**，但 **不建議在新代碼中使用**  
- 替代方案: **推薦用 Record View** ，取代 `RowSelect` 來決定載入的資料。


### **PreBuild**
- **執行時機**: 在所有 row 載入 **完成後** 只執行一次。
- **用途**: 
  - 隱藏/顯示頁面 (`Hide/Unhide Pages`)。
  - 設定 **Global 或 Component Scope 變數**。
  - **可設欄位預設值**
- **不建議** 使用 `Error()` 或 `Warning()`，以免影響 UI 流程。
 










![alt text](4.3_event_01.png)   
![alt text](4.3_event_02.png)   
![alt text](4.3_event_03.png)   
![alt text](4.3_event_04.png)   
![alt text](4.3_event_05.png)   
![alt text](4.3_event_06.png)   
![alt text](4.3_event_07.png)   
![alt text](4.3_event_08.png)   
![alt text](4.3_event_09.png)   
![alt text](4.3_event_10.png)   
![alt text](4.3_event_12.png)   
![alt text](4.3_event_13.png)   
![alt text](4.3_event_14.png)   
![alt text](4.3_event_15.png)   
![alt text](4.3_event_16.png)   
![alt text](4.3_event_17.png)   
![alt text](4.3_event_18.png)   

--------

--------

## 5. Writing PeopleCode Programs
- Writing PeopleCode Programs
- Writing Conditional Statements (continued)
- Activity 11: Selecting the Correct PeopleCode Events for Error Messages

--------

## 6. Using PeopleCode Variables
- Using PeopleCode Variables
- Incorporating Derived/Work Fields into Your Applications
- Describing Contextual Prompt Table Edits
- Activity 12: Calculating and Displaying Derived Values
- Activity 13: Reviewing the Setup for Contextual Prompt Table Edits

--------

## 7. Using PeopleCode Built-In Functions
- Using PeopleCode Built-In Functions
- Explaining String Functions
- Activity 14: Using PeopleCode Built-In Functions

--------

## 8. Writing User-Defined Functions
- Writing User-Defined Functions
- Calling User-Defined Functions
- Activity 15: Writing User-Defined Functions

--------

## 9. Explaining the Component Buffer
- Explaining the Component Buffer
- Activity 16: Determining the Contents of the Component Buffer

--------

## 10. Using Legacy Techniques to Access Data in the Component Buffer
- Using Legacy Techniques to Access Data in the Component Buffer

--------

## 11. Programming With Object-Oriented PeopleCode
- Programming With Object-Oriented PeopleCode
- Instantiating Objects of the components Buffer Classes
- RowNumber Property
- Activity 17: Using Methods and Properties of the Field Class

--------

## 12. Referencing Data in the Component Buffer
- Referencing Data in the Component Buffer
- Instructor Demonstration
- Using Shorthand Dot Notation
- Traversing Multiple Occurs Levels in the Component Buffer
- Activity 18: Traversing Objects and Data in the Component Buffer
- Activity 19: Looping Through Data in a Rowset
- Activity 20: Modifying Objects at Multiple Occurs Levels

--------

## 13. Using Additional Component Buffer Methods
- Using Additional Component Buffer Methods
- Using the Rowset Flush Method
- Working with Standalone Rowsets
- Using Other Component Buffer Methods
- Activity 21: Using the Select Method to Display Enrollments
- Activity 22: Flushing Data from a Rowset
- Activity 23: Using a Standalone Rowset to Calculate Effort Spent

--------

## 14. Creating and Using Application Classes
- Creating and Using Application Classes
- Using the PeopleCode Editor to Create and Modify Application Classes
- Using Application Classes
- Passing Parameters to Methods
- Activity 24: Creating and Using an Application Class
- Activity 25: Passing Method Parameters by Value
- Activity 26: Passing Method Parameters by Reference

--------

## 15. Extending and Implementing Base Classes
- Extending and Implementing Base Classes
- Activity 27: Extending a Built-in Class

--------

## 16. Executing SQL in PeopleCode
- Executing SQL in PeopleCode
- Creating SQL Definitions
- Using the SQL Class and SQL Objects
- Incorporating Meta-SQL in PeopleCode and SQL Definitions Executing SQL Using Record Objects
- Activity 28: Updating Effort Spent with a SQLExec Statement
- Activity 29: Updating Effort Spent with a SQL Definition
- Activity 30: Updating Effort Spent Using a SQL Object
- Activity 31: Choosing the Best SQL Option
- Activity 32: Using Object-Oriented Techniques to Execute SQL in PeopleCode

--------

## 17. Using PeopleCode to Create Charts
- Using PeopleCode to Create Charts
- Activity 33: Creating a Bar Chart

--------

## 18. PeopleCode Course Workshop
- PeopleCode Course Workshop

--------

## 19. PeopleSoft Peoplecode Course Review
- PeopleCode Cou