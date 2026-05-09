# Paris Itinerary Site Notes

## 溝通與工作方式

- 請用繁體中文回覆使用者。
- 行動過程要簡短講解，並在完成時整理重點。
- 修改前先確認使用者真正想改的是「行程內容」、「票務資訊」、「視覺呈現」或「程式結構」。
- 若涉及門票、開放時間、交通費、航班、餐廳營業或預約規則，這些資訊會變動；請先查官方或一手來源再更新內容。

## 專案概況

- 工作目錄：`C:\Users\User\Desktop\Codex\Paris`
- 主要呈現檔案：`paris.html`
- 同步備份/原始文字檔：`paris.txt`
- 目前瀏覽器開啟路徑：`file:///C:/Users/User/Desktop/Codex/Paris/paris.html`
- 這是一個單檔 HTML/React 行程網站，標題為「巴黎雙人行程規劃 2026」。
- 技術組成：HTML、Tailwind CDN、React 18 UMD、ReactDOM UMD、Babel Standalone、Leaflet CDN。
- 沒有 package.json、build step 或本地 dev server；直接用瀏覽器開 `paris.html` 即可。

## 程式結構

- 核心資料都在 `paris.html` 的 `<script type="text/babel">` 裡，主要物件是 `tripData`。
- `tripData.logistics`：航班、抵達/離開、飯店資訊。
- `tripData.ticketing`：Museum Pass、各景點票價、預約規則與購票連結。
- `tripData.foodGuide`：每日餐廳建議。
- `tripData.itinerary`：5/14 到 5/22 每日行程、提醒、活動、交通與注意事項。
- 下方 React components 只負責呈現：`OverviewView`、`TicketingView`、`FoodGuideView`、每日活動元件、地圖彈窗等。
- 修改資料時優先改 `tripData`，不要不必要地重構 React components。

## 已知重要事實與近期修正

- 使用者已購買 `Paris Museum Pass 4日券`，成本 `€105`。
- Museum Pass 無法改成 e-ticket，需於現場取實體票；目前安排 5/17 08:00 於 Paris City Vision Louvre 領取。
- 若 5/17 09:30 在羅浮宮首次掃描啟用 Museum Pass，96 小時效期至 5/21 09:30；5/20 奧塞與凱旋門仍在效期內。
- Museum Pass 覆蓋景點單買估算已修正為 `€166.5`，理論節省 `€61.5`。
- 已訂 `5/15 中午 Le Calife 午餐遊船`，不要再建議取消或改晚餐，除非使用者主動要求重排。
- CDG 到巴黎左岸第 6 區計程車公定價已修正為 `€65`；預約叫車可能另有附加費。
- 凡爾賽宮：持 Paris Museum Pass 應預約/取得免費 Passport 時段票；Passport 通常涵蓋宮殿、Trianon 與日間花園節目。不要寫成「PMP 不含花園秀、必須現場另付 €10-12」。
- 2026 巴黎交通票改制：前往凡爾賽使用 `Ticket Métro-Train-RER`，單程 `€2.55`，1-5 區鐵路/地鐵適用，機場除外。不要再以舊 T+ 票概念描述。
- 聖母院內部免費參觀；線上預約是建議以降低排隊風險，不是絕對強制。
- 票價已更正：傷兵院 `€17`、聖禮拜堂非 EEA 成人 `€22`、先賢祠 `€16`、巴黎地下墓穴 `€31`。

## 目前行程摘要

- 5/14：澳門出發，HKG/PVG 轉機，抵達 CDG，計程車入住 Hôtel l'Inattendu。
- 5/15：左岸、盧森堡公園、聖日耳曼，已訂 Le Calife 午餐遊船，下午拉丁區。
- 5/16：蒙馬特、瑪黑區、慶生晚宴。
- 5/17：現場取 Museum Pass，羅浮宮與橘園，Museum Pass Day 1。
- 5/18：聖母院、聖禮拜堂、先賢祠、傷兵院，Museum Pass Day 2。
- 5/19：凡爾賽宮與 Chanel 康朋街總店，Museum Pass Day 3。
- 5/20：奧塞、艾菲爾鐵塔、凱旋門、香榭大道，Museum Pass Day 4。
- 5/21：地下墓穴、第 6/7 區採購、正式晚餐。
- 5/22：退房、退稅預留時間、CDG 返程。

## 修改守則

- 若改 `paris.html`，請同步更新 `paris.txt`，兩者目前內容一致。
- 編輯時使用 UTF-8，保留繁體中文與法文重音字元。
- 這個檔案曾在 PowerShell 終端看起來像亂碼，但瀏覽器與 UTF-8 讀取正常；不要因終端顯示誤判內容損壞。
- 不要刪除 CDN script/link，除非改成完整本地化依賴並確定可離線運作。
- 不要把已確認的使用者事實改回未確認狀態，例如：5/15 午餐遊船已訂、Museum Pass 已購買且需現場取票。
- 完成修改後至少做這些檢查：
  - 搜尋舊錯誤字串是否殘留，例如 `€152.5`、`€47.5`、`€66`、`09:29 後失效`、`通行證不含花園秀`。
  - 用瀏覽器重新載入 `paris.html`，確認頁面標題與主要分頁可見。
  - 檢查瀏覽器 console 是否有此頁本身的 JavaScript error。

## 2026-05-05 網站精簡改造執行規則

- 本輪目標：把網站由「完整研究筆記」整理成「旅行前與旅行中可快速查閱的工具」。
- 執行順序：
  1. 美食推薦頁精簡：降低餐廳卡片與長篇說明的首屏密度。
  2. 購票預約頁任務化：以狀態、時程、官方連結優先呈現。
  3. 每日規劃摘要化：先顯示今日必做、風險、交通，再讓詳細內容展開。
  4. 最終同步與驗證：保持 `paris.html` 與 `paris.txt` 一致，並用瀏覽器檢查。
- 每完成一項，必須更新 `summary.md`，記錄完成內容、修改檔案與驗證結果。
- 原則：優先「收合與精簡呈現」，不要先刪除已整理好的行程資料；除非內容重複、過時或使用者明確要求刪除。
- 若涉及票價、開放時間、交通費、航班、餐廳營業或預約規則，更新實際內容前仍需查官方或一手來源。
