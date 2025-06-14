Activity 2-- 

**使用 PeopleCode Editor**
- 本活動回顧 PeopleCode Editor 的概述並試用多項功能。
- 你將學習如何使用編輯器撰寫與修改 PeopleCode 程式碼。
- 觀察自動格式化、語法驗證及自動備份等功能。

 

**活動詳細步驟**
- 按照具體操作步驟完成本活動。
- 開啟 PeopleCode 編輯器，載入 PSU_STUDENT_TBL 記錄。
- 運用學過的技巧開啟 PeopleCode 程式。

**開啟 PeopleCode 編輯器**
- 透過 App Designer，選擇「File」→「Open Record」開啟 PSU_STUDENT_TBL。
- 在記錄欄位「Same Address as Customer」的 FieldChange 事件中開啟 PeopleCode Editor。
- 點擊 FieldChange 檢查標記來進入編輯器。

**編輯器的文字顏色與格式**
- 編輯器使用不同顏色標示註解、關鍵字與字串。
- 可在「Edit Display Fonts and Colors」調整顏色設置。
- 具有 PeopleCode 的欄位與事件名稱會以粗體顯示。

**瀏覽記錄欄位與事件**
- 左側欄位清單顯示所有記錄欄位，粗體代表已應用 PeopleCode。
- 右側事件清單顯示所有事件，粗體表示該事件已含 PeopleCode 程式碼。
- 可選擇 STUDENT_NAME 欄位與 FieldEdit 事件進行編輯。

**輸入 PeopleCode 程式碼**
- 輸入 `If ^ = student_id Then Warning "Student name equals student ID";`，按「Save」儲存。
- 確保程式碼符合語法規範，例如 `If` 語句需縮排。
- 若語法有誤，編輯器會顯示錯誤訊息，如缺少 `And/If`。

**驗證與格式化 PeopleCode**
- 語法驗證時，編輯器會檢查 `^` 是否為目前欄位並自動補全記錄名稱。
- 若欄位屬於記錄，會自動添加記錄名稱；若不屬於，則顯示錯誤訊息。
- 編輯器統一函式、類別與變數的大小寫，並根據第一個出現的寫法調整。

**程式碼可讀性改進**
- 編輯器會自動縮排，提高程式碼可讀性。
- 引號內的文字不受格式化影響，可自由輸入內容。
- 若變數未宣告，編輯器會顯示自動宣告訊息，預設類型為 `Any`。


**變數宣告與語法驗證**  
- 雖然非必需，但建議宣告所有變數，以確保類型檢查與語法驗證。  
- 特別是物件型變數，宣告可避免屬性與方法使用上的錯誤。  
- PeopleCode 會驗證大部分宣告的物件類型，確保資料類型匹配。  

**編輯功能**  
- PeopleCode 編輯器提供剪下、複製、貼上、復原等標準文本編輯功能。  
- 相關選項可在「Edit」選單中找到，如 Undo、Redo、Cut、Copy、Paste 等。  
- 可使用快捷鍵提升操作效率，例如 Ctrl + Z 進行復原。  

**PeopleCode 定義的存儲**  
- PeopleCode 定義不會與記錄定義一起存儲，而是保存在 PeopleTools 資料表中。  
- 可在 PeopleCode 編輯器中查看並管理 PeopleCode 程式碼。  
- 這種設計有助於統一管理程式碼與版本控制。  

**F1 取得 PeopleCode 說明**  
- 在編輯器中選擇「Warning」，按 F1 鍵可開啟 PeopleCode 語言參考文件。  
- F1 說明是區分大小寫的，錯誤輸入可能導致「404 Not Found」錯誤。  
- 可用來查詢內建函式、系統變數、PeopleCode 語法與 PeopleTools API。  

**PeopleCode 開發者指南**  
- F1 說明可用於相關功能與對話框，如 PeopleCode 編輯器的使用說明。  
- 可選擇瀏覽器開啟文件，例如 Google Chrome。  
- 若有新版指南，可選擇最新版本，但可能失去上下文關聯性。  

**版本更新與 Web 伺服器調整**  
- 若需查看新版的 PeopleCode 說明，需更新 Web 設定。  
- 可在 PeopleTools → Web Profile Configuration 修改 Help URL。  
- 若要變更生效，須重新啟動 PIA 網域。  

**開發工具的幫助位置設置**  
- 在 PeopleTools → Administration → PeopleTools options 內設定幫助文件位置。  
- 修改 Help URL 可更新 App Designer、Data Mover 及 PIA 的參考文件。  
- 若修改成功，開啟 F1 將會指向新版文件。  

**F1 Help 測試與結果**  
- 重新設定 Help URL 後，若未重啟 PIA，仍會指向舊版本文件。  
- 測試變更版本號可能無法運作，但值得一試。  
- 若要完整套用更新，仍需重啟 Web 伺服器。  


**Web 伺服器設定變更**  
- 變更 Help URL 後，需重啟 Web 伺服器並重新登入，才會生效。  
- 若未重新啟動 PIA，依舊會指向舊版說明文件。  
- 這是更改 PeopleTools 設定時需注意的步驟。  

**檢視記錄與 PeopleCode 定義**  
- 右鍵點擊 PSU_STUDENT_TBL，選擇「View Definition」可檢視記錄定義。  
- 可檢視記錄欄位屬性與其他相關設定。  
- 程式內的定義皆可透過右鍵選單檢視對應的 PeopleCode。  

**檢視函式與類別定義**  
- 右鍵點擊函式名稱，選擇「View Function」可開啟該函式所在的程式。  
- 右鍵點擊類別名稱，選擇「View Application Package」或「View Application Class」可檢視類別定義。  
- 這些功能可用來快速導航至相關的應用程式類別與函式。  

**拖曳功能**  
- PeopleCode 編輯器支援拖曳功能，可拖曳專案檢視中的元素至編輯區。  
- 可拖曳記錄定義、欄位定義、元件定義等至編輯區，但不需儲存。  
- 可跨 PeopleCode 程式進行拖曳，便於程式編寫。  

**PeopleCode 自動儲存機制**  
- PeopleCode 編輯器在每次輸入時自動備份，存放於 TMP 目錄。  
- TMP 目錄通常位於 Windows 系統的 TMP 路徑，而非 C:\Temp。  
- 可透過 Windows 指令 `set` 來檢視 TMP 目錄的實際位置。  

**存取暫存備份檔案**  
- 若 TMP 目錄內有編號的資料夾，應開啟該資料夾來查找備份檔案。  
- 自動儲存檔案名稱格式為 `PPCMMDDYY_HHMMSS`，其中 MMDDYY 為日期，HHMMSS 為生成時間。  
- 儲存 PeopleCode 後，備份檔案將被刪除，可嘗試輸入新內容並再次檢視。  


**查看 PeopleCode 暫存資料**  
- 進入 TMP 目錄，查看 PeopleCode 的自動備份檔案。  
- 備份檔案名稱包含日期與時間，可用記事本開啟。  
- 每次輸入時，編輯器會將資料備份至 TMP 目錄。  

**修改 PeopleCode 編輯器字體與顏色**  
- 進入 Application Designer，確保 PeopleCode 程式為作用中的定義。  
- 選擇「Edit」→「Display Fonts and Colors」來調整字體與顏色。  
- 預設關鍵字顏色為藍色，可自行更改為其他顏色。  

**結束 PeopleSoft Application Designer**  
- 選擇「File」→「Exit」退出 PeopleSoft Application Designer。  
- 下一個活動將開啟新的 PeopleSoft Application Designer 工作階段。  

