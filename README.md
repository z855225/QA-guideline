# QA 入門手冊
## QA 的特質
1. 細心，能站在使用者角度思考
2. 有日常愛用的產品，並常常感到不滿，覺得哪裡可以做得更好
3. 喜歡研究、使用各種網頁、App
4. 喜歡試用各種新服務、產品，對商業模式、功能有想法，提出改善
<img width="1083" alt="截圖 2024-10-26 下午3 29 46" src="https://github.com/user-attachments/assets/a9619151-2f9c-49ba-a377-c4f1a9f24827">

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
<img width="1162" alt="截圖 2024-10-26 下午3 33 25" src="https://github.com/user-attachments/assets/6873753a-efa1-49b0-8f0e-5488023bf89d">

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
# QA 專案工作流程
## 環境資訊
Staging (開發環境) → Alpha (測試環境) → Production (正式環境)
## 時程
https://whimsical.com/sprint-8-7-NpDawUWH9TYBDfqpMfhGgJ
<img width="1367" alt="截圖 2024-10-26 下午3 37 57" src="https://github.com/user-attachments/assets/916c4fa8-0f41-49c4-a7b1-5ee210d3cf9f">

## Hotfix (Day 1 ~ Day 8)
有緊急狀況要修復，或是上個 sprint 未完成的事項，在本次 sprint 一週後會安排一個
Hotfix  
流程: 直接上到 alpha 給 QA 驗證 → 上到 production  
有發生過需要 hotfix 的 bug (需求不算) 且 regression test case 沒涵蓋到，需新增 test
case
## Staging feature testing (Day 1 ~ Day 8)
1. QA 產出 test case，可參考 DOD，過程中可以發現 spec 設計有無問題可即時反應給 PO
2. 測試這個 sprint 的 features
3. 一有 feature 完成就可以馬上交給 QA 測試
4. 必須在 Day 8 以前開發完成所有 features 並要留 QA 測試時間，真的來不及 PO 判斷要回 backlog 或是走 hotfix
5. 期間測出的 bug 盡量在 Staging 修復完畢，並重新測試通過，真的來不及可在下一階段的 Alpha 執行
6. Day 8 上到 Alpha 後盡量保持 code freeze (理想狀態，如果 8 天處理不完，可能估點太樂觀)
## Alpha integration + regression testing (Day 9 ~ Day 15)
1. 測試這個 sprint 的 features
2. 測試可能因新增功能而產生的舊功能 side effect
3. 測試 P1 test case (重要的 絕對不能出錯的功能，例如 登入、註冊、播放影片 )
4. 期間測出或 Staging 遺留的 bug 必須在 Alpha 修復完畢，並重新測試通過，真的來不及由團隊評估是否延遲 production 上線或移至 backlog 在之後的 sprint 排修 (假設有 task 在這個階段才完成，請跳過 staging，直接 merge 到 alpha 讓 QA 測試)
## Production sanity check (Day 15)
1. 簡單測試這個 sprint 的 features
2. 測試 P1 test case (重要的 絕對不能出錯的功能，例如 登入、註冊、播放影片 )
3. 排除會影響營運的測項，例如在客戶的 domain 新增課程
## 測試期間發現的 production bug
一樣放在目前的 sprint board + backlog 裡面，並決定是否進行 hotfix 或隨本次 sprint release 或留在 backlog 後續排修
## 每個測試階段完成會出 QA report
使用 asana 的 Reporting 功能，分三個圓餅圖，並再用嚴重程度細分 (S1 ~S3)
1. 本次 sprint 新產生的 bug
2. production 已有的舊 bug
3. 本次 sprint 必修復的 bug (此圓餅圖清空才能 release)

Staging, Alpha, Production 會有相對應的 TestRail 的 test run
## QA 行事曆
使用 google 行事曆讓 QA 成員知道目前要做什麼事
# Automation Test 規劃
## 目標
把所有 test case 都自動化，省去 QA 手動測試 regression 的時間，進而縮短 sprint 時間，加快產品交付速度
## 概況
TestRail test case 連結 (隨著每個 sprint new feature 持續增加中)  
Filter -> Automation Type -> Cypress UI，可以篩選出已自動化的 case
## coding style
和前端使用同一套 eslint 規則
## 階段一
* QA 不分手動自動，希望能互相支援
* 已經自動化的 case 標記 Automation Type: Cypress UI，regression 手動測試就可以過濾出來排除掉
* 先不做 API 測試，雖然金字塔理論告訴我們 API 要比較多，但是在人力有限的情況 UI 這塊還是放不掉，只要把 UI 做好也能 cover API 測試的部分
* 先做 web UI「Smoke & Sanity」 test。test case type 會分成 「Functional」和
「Smoke & Sanity」兩種，Functional: 有 new feature 時會做的詳細測試，Smoke &
Sanity: regression 時做的重點大方向測試
* 測試結果串接 TestRail 自動建立 test run。在 QA local 執行，時機點在手動測試 regression 前
* 例行的壓力測試
### acceptance criteria:
「Smoke & Sanity」test case 自動化覆蓋率到 80% 以上
## 階段二
* 串接 QA 自己的 CI
* 發生 fail 誤報需先隔離在 local 執行，修復穩定後再上 CI
### acceptance criteria:
automation fail 誤報率小於 10 %
## 階段三
* 和 DEV CI 串接
實作「Functional」test case
* App automation，再走一次階段一、階段二
### acceptance criteria:
維持所有 test case 自動化覆蓋率 80%，automation fail 誤報率小於 10 %
