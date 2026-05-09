# Paris Site Simplification Summary

## 目標

把巴黎行程網站由「完整研究筆記」整理成「旅行前與旅行中可快速查閱的工具」。本輪採逐項完成、逐項記錄方式進行。

## 執行項目

| 項目 | 狀態 | 摘要 |
| --- | --- | --- |
| 1. 美食推薦頁精簡 | 已完成 | 預設只顯示每餐首選與備案；第三選與全局名店改為展開式。 |
| 2. 購票預約頁任務化 | 已完成 | 改為關鍵數字、任務狀態、處理時程與官方連結優先。 |
| 3. 每日規劃摘要化 | 已完成 | 每日時間軸前新增三格摘要；長風險提醒改為展開式。 |
| 4. 最終同步與驗證 | 已完成 | `paris.html` / `paris.txt` 已同步，瀏覽器分頁驗證通過。 |

## 變更紀錄

### 2026-05-05

- 建立本檔作為每項改造的完成紀錄。
- 已在 `AGENTS.md` 追加本輪網站精簡改造的執行規則。
- 完成美食推薦頁精簡：
  - 「評分數據偏差風險與排程聲明」改為短版「用餐決策原則」。
  - 每餐預設顯示 2 間：首選與備案；第 3 間改為「顯示更多備案」展開。
  - 「巴黎指標性美食 20 選」改為收合區塊，避免搶走每日動線推薦的注意力。
  - 保留原餐廳資料與 Google Maps 連結，僅精簡預設呈現。
- 完成購票預約頁任務化：
  - 上方改為三個關鍵數字：Museum Pass 已購買成本、覆蓋景點估算、理論節省。
  - 原完整分析與注意事項改為「查看完整票務提醒」展開區。
  - 每張票務卡加入狀態標籤：已訂、需搶票、需預約、可彈性、建議預約。
  - 卡片優先顯示單買票價、處理時程與官方網站連結。
- 完成每日規劃摘要化：
  - 新增 `DaySummary`，於每日時間軸前顯示「今日主軸」、「今日必留意」、「交通起手式」。
  - 摘要由現有 `tripData.itinerary` 自動取得，不另建重複資料。
  - 原每日風險提醒改為展開式，保留資訊但降低預設閱讀壓力。
- 完成最終同步與驗證：
  - `paris.html` 與 `paris.txt` 已同步。
  - 已搜尋舊錯誤字串與被替換的舊美食頁長標題，未發現殘留。
  - 已用 in-app browser 重新載入 `paris.html`，確認「每日規劃」、「事前準備」、「購票預約」、「美食推薦」分頁均可見並顯示新內容。
  - 瀏覽器 console 未見此頁本身的 JavaScript error。

### 2026-05-09

- 更新 5/14 抵達日早晨交通：
  - 將原「02:40 計程車至澳門口岸、夜間金巴、香港口岸轉乘」改為「04:30 由海洋花園搭跨境專車直接前往香港國際機場」。
  - 移除不再適用的金巴夜間班次與口岸轉乘提醒，改為確認司機、車牌、上車點、證件與行李件數。
  - `paris.html` 與 `paris.txt` 已同步更新。
- 啟動 iPhone 友善 Web App 改造：
  - 新增設計規格與實作計畫：`docs/superpowers/specs/2026-05-09-iphone-pwa-mobile-design.md`、`docs/superpowers/plans/2026-05-09-iphone-pwa-mobile.md`。
  - 新增 PWA 檔案：`manifest.webmanifest`、`service-worker.js`、`icons/paris-icon.svg`、`icons/paris-icon-180.png`、`icons/paris-icon-512.png`。
  - `paris.html` 加入 iPhone Safari metadata、Apple touch icon、service worker 註冊條件、手機旅行模式卡片與 iPhone safe-area 底部導覽。
  - 手機版底部導覽提供「今日、行程、票務、美食、地圖」快速入口，今日卡片保留「事前準備」入口。
- 補齊部署入口與 iPhone 使用文件：
  - 新增 `index.html` 作為部署根目錄入口，會自動開啟 `paris.html`。
  - 新增 `IPHONE_WEB_APP.md`，記錄 iPhone Safari「加入主畫面」流程、HTTPS 限制與隱私提醒。
  - `service-worker.js` 已納入 `index.html` 快取。
- 完成公開部署：
  - 建立公開 GitHub repo：`https://github.com/kennykam2004/paris-2026-itinerary`
  - 啟用 GitHub Pages：`https://kennykam2004.github.io/paris-2026-itinerary/`
  - 公開部署包位於 `public-deploy`，只包含網站必要檔案，未包含 `.superpowers/`。
- 修正手機地圖遮罩問題：
  - 地圖改成手機版可關閉的底部面板，加入大按鈕「行程 / 票務 / 關閉地圖」。
  - 點底部導覽切換頁面時，會先關閉地圖，避免地圖卡住其他分頁。
