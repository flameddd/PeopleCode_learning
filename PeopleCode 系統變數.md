PeopleSoft **PeopleCode 系統變數 (`System Variables`)** 是在使用者登入時自動建立，可在程式中存取環境資訊。所有系統變數都以 **`%`** 符號開頭，以下是完整的系統變數列表：

### **時間與日期相關 (`Date & Time Variables`)**
- **`%Date`**：返回當前**伺服器日期**（`Date` 型別）。
- **`%Time`**：返回當前**伺服器時間**（`Time` 型別）。
- **`%DateTime`**：返回當前**伺服器日期時間**（`DateTime` 型別）。
- **`%ClientDate`**：返回**使用者當前時區調整後的日期**。
- **`%ClientTimeZone`**：返回**使用者當前時區**（3 字元格式）。

### **環境上下文 (`Context Variables`)**
- **`%Page`**：返回當前**頁面名稱**。
- **`%Component`**：返回當前**元件名稱**。
- **`%Menu`**：返回當前**選單名稱**。
- **`%Mode`**：返回當前**頁面模式**（`"A"` 表示 **新增模式**，`"U"` 表示 **更新模式**）。
- **`%Portal`**：返回當前**使用的門戶**。
- **`%Node`**：返回當前請求物件的**節點名稱**。
- **`%RouteLevel`**：對應**選單系統的路由層級**。

### **使用者資訊 (`User Information Variables`)**
- **`%UserId`**：返回當前**登入的使用者 ID**。
- **`%Language_User`**：返回當前**使用者的語言設定**（從登入畫面選擇）。
- **`%Currency`**：返回當前**使用者的偏好貨幣**。

### **系統行為 (`System Process Variables`)**
- **`%Request`**：返回**當前請求 (`Request`) 的引用**。
- **`%Content_ID`**：返回當前**內容 (`Content`) 的識別碼**（字串）。
- **`%ContentType`**：返回當前**內容類型**（字串）。

### **應用類別相關 (`Application Class Variables`)**
- **`%This`**：指向**當前物件 (`Current Object`)**（適用於應用程式類別）。
- **`%Super`**：指向**父類別物件 (`Superclass Object`)**（用於繼承）。
 