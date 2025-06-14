Activity 3-- 

以下是該 PeopleSoft 文章的條列式摘要：

### 1. **PeopleCode 程式除錯概述**
- 介紹如何使用 PeopleCode 除錯工具來分析程式。
- 主要關注在 PSU_PO_DTL 記錄的 ORDER_LINE_NBR 欄位的 RowInsert 事件。
- 設定斷點並執行應用程式，觀察除錯工具提供的資訊與選項。

### 2. **活動概覽**
- 在 **PeopleSoft Application Designer** 三層模式下開啟 PeopleCode 程式。
- 變更連線類型為 **Application Server**，使用 T1B85701 資料庫。
- 使用 PTCODE 帳號登入後，開始進行程式除錯。

### 3. **活動詳細步驟**
- 開啟 **PSU_PO_DTL** 記錄，檢視 ORDER_LINE_NBR 欄位的 PeopleCode。
- 切換至 **RowInsert 事件**，確保未選錯為 RowDelete。
- 關閉輸出視窗 (Alt+1) 以擴展除錯視窗範圍。

### 4. **啟動除錯工具**
- 進入 **Debug Mode**，開啟 **Call Stack** 與 **Local Variables** 窗格。
- 若有先前設定的斷點，系統會自動恢復。
- 開啟 **Component Buffer** 以檢視元件資料，可調整視窗大小以利觀察。

### 5. **設置斷點**
- 在程式碼第 3 行 **"If LINE > MAXLINE Then"** 設定斷點。
- 使用 **F9** 或 **Debug → Toggle Break at Cursor** 設定紅色斷點標記。
- 斷點觸發時，應用程式會停在相應的執行位置。

### 6. **在瀏覽器測試**
- 進入 **Purchasing → Maintain Purchase Orders**，選擇 **Order 00000029**。
- 在第二行插入新資料列，按 **+** 按鈕新增一行，確認數值為 1 並按 OK。
- 程式遇到斷點時，PeopleSoft Application Designer 會閃爍或自動取得焦點。


### 7. **程式除錯的視覺指標**
- **App Designer 閃爍**表示程式執行到斷點並暫停。
- 在除錯器中，黃色箭頭標示當前執行位置，紅色斷點標記被綠色箭頭覆蓋，顯示當前執行的 PeopleCode 陳述式。

### 8. **檢視變數的值**
- 在 **PeopleCode 編輯器**內，可**滑鼠懸停**於變數查看其當前值，如 `&I` 變數顯示數值 `1`。
- 也可懸停於欄位名稱來檢視當前欄位值，例如 `ORDER_LINE_NBR` 目前為 `0`。

### 9. **除錯面板與數據檢視**
- **Local Variables 面板**預設開啟，顯示**區域變數與物件屬性**，可展開物件以查看更多資訊。
- 也可開啟 **全域變數、元件變數與函式參數面板**。
- 使用 **F8** 可逐行執行程式碼，箭頭指示目前執行行，變數數值隨迴圈變化。

### 10. **Component Buffers 面板與資料結構**
- **Component Buffer** 顯示所有元件數據，可展開來檢視記錄 (`GetRecord`)、欄位 (`GetField`) 等資料。
- **不要展開 ParentRowsets 或 ParentRow**，可能導致無限迴圈。

### 11. **動態變數變化**
- 使用 **F8** 逐步執行程式時，可查看 `MAXLINE` 和 `LINE` 變數如何變化。
- `&I` 變數會隨迴圈增加，數值從 `1` 變成 `2`，而 `MAXLINE` 也會隨條件判斷更新。

### 12. **記錄層級結構**
- **RowSet 由行組成**，可展開檢視其方法與屬性，如 `RowCount, ActiveRowCount` 等。
- **行可能包含記錄或子 RowSet**，每個記錄內包含欄位，展開 `GetFields` 可看到欄位名稱與其當前值。

### 13. **建立 Debug 記錄**
- 在 **Debug → Options → Log Options** 選擇 **Execution Trace** 記錄每行程式碼執行情況。
- 按 **ALT+1** 開啟 Debug 記錄，觀察 PeopleCode 日誌。

### 14. **除錯第二個程式**
- **清除現有斷點**：在 **Debug → Edit Breakpoints** 點擊 **Remove All** 來移除所有斷點，然後點擊 **OK**。



### 15. **終止程式執行**
- 在 **Debug → Abort Running Program** 終止程式執行，以釋放資源。
- 關閉 **PeopleCode 編輯器** 和 **PSU_PO_DTL 記錄定義**，減少工作區混亂。
- 應用程式中確認程式終止訊息，點選 **OK** 並返回主畫面。

### 16. **開啟 PSU_STUDENT_TBL 記錄**
- 開啟 **PSU_STUDENT_TBL**，檢視 **STUDENT_ID 欄位的 PeopleCode**。
- 在 **事件選擇區** 選擇 **SavePreChange**，確保使用正確事件。

### 17. **檢視與設置斷點**
- 右鍵 **assign_student_id 函式**，選擇 **檢視函式程式碼**。
- 在 **STUDENT_ID = LAST_STUDENT + 1** 處按 **F9** 設置斷點。

### 18. **測試新增學生資料**
- 在 **Students → Personal Information** 中新增學生資料。
- **輸入姓氏、名字、客戶 ID**，按 **Save**。
- 執行 Save 時，應用程式進入除錯模式，**App Designer 閃爍**。

### 19. **檢視變數與修改值**
- **懸停於 LAST_STUDENT 變數** 以檢視當前值，例如 `3001`。
- **修改變數值** 為 `4001`，確保輸入數字且不含雙引號。

### 20. **檢視 Call Stack 面板**
- 在 **Call Stack 面板** 中檢視函式呼叫順序。
- 使用 **F8** 執行 PeopleCode，每次點擊皆可檢視堆疊變化。
- 當函式執行完畢時，會**從堆疊中移除**。



### 21. **檢視新建學生 ID**
- 在瀏覽器中檢查 **新建立的學生 ID**，應比原值多 1，例如 `4002`。
- 使用 **F8** 最後一步執行程式，檢視學生 ID 變化。

### 22. **退出 PeopleCode 除錯模式**
- 在 **Application Designer** 中，選擇 **Debug → Edit Breakpoints**，點擊 **Remove All** 清除所有斷點。
- 進入 **Debug → Options → Log Options**，取消 **Each statement** 勾選，然後按 **OK**。

### 23. **結束除錯模式**
- 在 **Debug → Exit Debug Mode** 退出 PeopleCode 除錯模式。
- 在 **File → Exit** 完全關閉 **PeopleSoft Application Designer**，準備開啟新的設計器會話。

