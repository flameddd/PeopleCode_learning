PeopleCode 在 **PeopleSoft** 系統中支援多種事件（Event），這些事件會在 **不同的元件處理階段** 觸發。總體上，PeopleCode 事件可分為以下幾個主要類別：

---

### **1. Field Level（欄位層級）事件**
這類事件與 **特定欄位的變更或驗證** 相關：
- **FieldDefault**：在欄位的預設值初始化時執行。
- **FieldFormula**：可用於計算欄位值，類似於 SQL 的計算欄位，但可執行更複雜邏輯。
- **RowInit**：當行被載入到緩衝區時執行，通常用於計算派生欄位。
- **FieldEdit**：用於欄位輸入驗證，若條件不符合可顯示錯誤或警告。
- **FieldChange**：當欄位變更後執行，通常用於更新相關欄位值或計算。

---

### **2. Record Level（記錄層級）事件**
這類事件影響 **整個記錄（Row）的行為**：
- **SaveEdit**：在儲存前執行，用於驗證記錄的完整性。
- **SavePreChange**：在儲存到資料庫之前執行，通常用於計算或修改記錄欄位。
- **SavePostChange**：在資料儲存到資料庫後執行，適用於後續處理，如更新外部系統。

---

### **3. Row Level（資料列層級）事件**
這類事件涉及 **資料列的新增或刪除**：
- **RowInsert**：在新增資料列時執行，可用於設定預設值或覆蓋預設處理行為（如 Effective Date）。
- **RowDelete**：在刪除資料列時執行，通常用於重新計算數據或防止刪除特定行。

---

### **4. Component Level（元件層級）事件**
這些事件影響 **PeopleSoft 元件的運作**：
- **PreBuild**：在元件載入前執行，用於初始化變數或進行存取控制。
- **PostBuild**：在元件載入後執行，通常用於 UI 控制或資料初始化。
- **ComponentSavePreChange**：與 SavePreChange 類似，但影響整個 Component。
- **ComponentSavePostChange**：與 SavePostChange 類似，但影響整個 Component。

---

### **5. Workflow（工作流程）事件**
這類事件涉及 **PeopleSoft 工作流（Workflow）運作**：
- **TriggerBusinessEvent**：用於觸發業務事件（如通知、外部系統交互）。
- **Workflow**：與 PeopleSoft Workflow 結合，用於業務流程處理。

---

### **6. Message Level（訊息層級）事件**
PeopleCode 也可與 **Integration Broker（IB）訊息處理** 互動：
- **SubscribeMessage**：當訊息被接收時執行，用於解析 XML 或處理資料同步。
- **PublishMessage**：當 PeopleSoft 發送訊息時執行。

---

### **7. Rowset Level（資料集合層級）事件**
這類事件影響 **Rowset（多行集合）處理**：
- **RowsetScroll**：當使用者滾動 Grid 或 Scroll 區域時執行，可用於動態載入資料。

---

### **總結**
PeopleCode 事件可分為以下類別：
1. **欄位層級（Field Level）**
2. **記錄層級（Record Level）**
3. **資料列層級（Row Level）**
4. **元件層級（Component Level）**
5. **工作流程（Workflow）**
6. **訊息層級（Message Level）**
7. **資料集合層級（Rowset Level）**

這些事件組成了 **PeopleSoft 的事件驅動架構**，可根據不同的業務需求進行程式邏輯設計！你有特定的事件想要深入探討嗎？ 😃