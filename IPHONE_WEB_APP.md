# iPhone Web App 使用與部署說明

## 目前狀態

這個資料夾已具備 iPhone 友善 Web App 所需的基本檔案：

- `index.html`：部署根目錄入口，會自動開啟 `paris.html`
- `paris.html`：主要行程 App
- `manifest.webmanifest`：PWA 設定
- `service-worker.js`：快取 App shell
- `icons/`：主畫面圖示

公開 HTTPS 網址：

https://kennykam2004.github.io/paris-2026-itinerary/

## iPhone 加入主畫面方式

1. 用 iPhone 的 Safari 開啟公開網址：`https://kennykam2004.github.io/paris-2026-itinerary/`
2. 等頁面載入完成。
3. 點 Safari 下方分享按鈕。
4. 選「加入主畫面」。
5. 名稱建議保留 `Paris 2026`。

注意：`file://` 本機檔案可以在電腦預覽，但 iPhone 不會把它當成正式可安裝 PWA。正式使用請開啟上方 HTTPS 網址。

## 隱私提醒

這份行程包含日期、飯店、航班與每天動線。部署前請先決定是否接受公開網址。

建議選項：

- 私人使用：部署到需要登入或可設定密碼的平台。
- 半公開使用：部署到不容易猜到的網址，但知道連結的人都能看。
- 公開使用：GitHub Pages 等公開靜態網站，最簡單但不適合敏感行程。

## 可部署檔案

部署時至少需要上傳：

- `index.html`
- `paris.html`
- `manifest.webmanifest`
- `service-worker.js`
- `icons/`

可一併保留：

- `paris.txt`
- `summary.md`
- `docs/`

不需要上傳：

- `.superpowers/`
