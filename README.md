# QA 入門手冊
## QA 的特質
1. 細心，能站在使用者角度思考
2. 有日常愛用的產品，並常常感到不滿，覺得哪裡可以做得更好
3. 喜歡研究、使用各種網頁、App
4. 喜歡試用各種新服務、產品，對商業模式、功能有想法，提出改善
## QA 日常
1. 釐清這個 sprint 要做的 task，閱讀分析 PRD (Product Requirement Document)
2. 根據 PRD 寫 test case
3. 挑選適合的 test case 建立 test run（即多個 test case 的集合）
    * 第一階段測試環境 (staging) feature test  
    測試這次 sprint 做的新功能
    * 第二階段測試環境 (alpha) regression test  
    測試這次 sprint 做的新功能 + 現有的舊功能
    * 正式環境 (production) sanity test  
    測試重點功能，由於是正式環境所以不能測會影響營運的項目，例如更改客戶訂單、修改客戶的任何資料
4. 依照 test run 執行測試
    * 測試前先確認測試目標版本、環境正確才不會做白工
    * 測試中不只要按照 test case 執行，還要做延伸發想可能發生 bug 的地方
5. 回報問題
6. 追蹤、驗證問題
7. 撰寫 automation script
    * 將不太會變動的舊功能自動化，以程式測試節省時間
8. 即時處理客服、業務反應的問題
    * 代表在測試期間未發現的漏網之魚 bug 被使用者遇到，可能對產品或公司造成負面影響，需優先處理，用最快速度確認找出重現方法，使用者只會反應簡單的結果，
必須找出重現 bug 的詳細步驟並記錄在 bug 管理系統 (這個動作簡稱開單、開 ticket) 方便 dev 修復及後續追蹤
    * 不會有 100% 零 bug 的系統，QA 的目標是使 bug 趨近於零，遇到問題不要緊張怕被罵，當前最重要的是處理解決問題，之後再來分析為什麼測試沒抓出問題，下次能怎麼避免，會越來越好
## 技能樹
https://whimsical.com/qa-32xdf3sa8QVmjJ46Sd9DXC
## 工作流程
sprint 為 15 天一個週期循環  
https://whimsical.com/Pjp7VjALXQZSucHugFjkNK
## test case
使用心智圖寫 test case  
使用 TestRail 撰寫  
## 測試種類
### Feature Test
對新開發的功能做詳細的測試，確保功能有符合需求
### Smoking Test
最簡單基本的測試，如果連 smoking test 都沒通過，後面再細節的功能都可以先不用測，等問題修復再繼續測下去。例如登入壞掉，就不用再去想其他測試
### Integration Test
兩個功能單獨測試可能沒問題，但一起整合測試有時會有其他問題  
http://youtube.com/watch?v=0GypdsJulKE
## 如何回報問題
### Ticket 結構
#### Title
* 最前加中括號填上屬於的 function 方便之後查找，例如: [iOS] [上課] [我的課程] [篩選]
* 標題描述實際狀況，而非預期狀況
* 使用最少能清楚描述 bug 整體情況的字數
#### 相關討論連結
* 如果在 slack 有相關討論可以附上連結
#### Failure rate
* 如果 bug 不是 100% 發生，可以附上機率，例如: 2 out of 5 times
* 如果是 100% 發生就不用特別寫
#### Environment
* web / app 版本
* 環境 staging / alpha / production
* 特殊裝置才會發生的 bug，附上 device 資訊
#### Step
* 重現 bug 的操作步驟
#### Actual Result
* 實際結果
#### Expected Result
* 預期結果
#### 附檔
* 時間允許的情況下盡量附上圖片或影片幫助理解