在 **PeopleCode** 中，**Component Buffer** 是儲存目前作用中元件（Component）資料的記憶體區域。當使用者開啟頁面時，系統會載入所有相關的記錄（Record）並組織成 **緩衝區（Buffer）**，以便 PeopleCode 存取和操作。

### **Component Buffer 結構**
Component Buffer 由 **不同層級（Scroll Levels）** 組成：
1. **Level 0（根層）**：包含主要記錄（Primary Record），通常是元件的核心資料。
2. **Level 1、2、3（子層）**：用於管理 **子記錄（Child Records）**，例如明細資料或相關顯示欄位。

### **存取 Component Buffer**
PeopleCode 提供多種方式來存取 Component Buffer：
- **`GetLevel0()`**：取得 Level 0 的 **Rowset**（行集合）。
- **`GetRowSet(Scroll.<RecordName>)`**：取得指定 Scroll Record 的 Rowset。
- **`GetRow(n)`**：取得特定索引的 Row（行）。
- **`GetRecord(Record.<RecordName>)`**：取得指定 Record（記錄）。
- **`GetField(Field.<FieldName>)`**：取得指定 Field（欄位）。

### **範例**
以下是存取 Level 1 記錄的範例：
```peoplecode
Local Rowset &RS_Level0, &RS_Level1;
Local Row &Row_Level0, &Row_Level1;
Local Record &Rec_TaskRsrc;
Local Field &Fld_PctAvail;

&RS_Level0 = GetLevel0();
&Row_Level0 = &RS_Level0.GetRow(1);
&RS_Level1 = &Row_Level0.GetRowSet(Scroll.PSV_TASK_RSRC);
&Row_Level1 = &RS_Level1.GetRow(1);
&Rec_TaskRsrc = &Row_Level1.GetRecord(Record.PSV_TASK_RSRC);
&Fld_PctAvail = &Rec_TaskRsrc.GetField(Field.PCT_AVAILABLE);
```
這段程式碼逐步存取 **Level 0 → Level 1 → Record → Field**，適用於動態存取元件資料。

### **應用場景**
- **動態存取頁面資料**：在事件（Event）中操作元件資料，例如 `RowInit` 或 `FieldChange`。
- **驗證與計算**：根據不同層級的資料進行計算或驗證。
- **資料同步**：確保不同層級的資料一致性。


