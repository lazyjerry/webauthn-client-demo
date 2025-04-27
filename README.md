# WebAuthn Client Demo 🔑

一個最小可行的 **Passkey / WebAuthn** 前端示範，  
搭配 Cloudflare Workers 後端，即可實現無密碼註冊與登入。

👉 [前端 DEMO](https://webauthn-client-demo.pages.dev/)  
👉 [後端 DEMO（可能失效）](https://webauthn.crazyjerry.workers.dev)

> ⚡ 若後端 demo 無法連線，請參考 [lazyjerry/webauthn](https://github.com/lazyjerry/webauthn) 自行部署 Cloudflare Workers！

---

## 注意事項 Important Notes

- 本專案最初使用了較舊版 [`@passwordless-id/webauthn`](https://github.com/passwordless-id/webauthn)：

  ```text
  https://cdn.jsdelivr.net/npm/@passwordless-id/webauthn/dist/webauthn.min.js?module

  •	該版本存在 API 不一致與無法直接 encode 的問題。
  •	目前已更新至 2.3.0 版本，並以原生 ESM 模式載入：
  ```

https://cdn.jsdelivr.net/npm/@passwordless-id/webauthn@2.3.0/+esm

    •	詳細差異與最佳實踐，請參考：
    •	GitHub Repo
    •	WebAuthn.io 官方測試站
    •	本專案 Server 端來自 AprilNEA/webauthn-workers 進行修改，

已部署於 Cloudflare Workers + KV，支援完整註冊、登入流程與 counter 防呆機制。

⸻

特色 Features
• 純前端
使用原生 ES Modules ＋ TailwindCSS，無需打包器。
• 完整 WebAuthn 流程
• /register/challenge → client.register() → /register/verify
• /login/challenge → client.authenticate() → /login/verify
• CORS／Counter 容錯皆已處理
支援所有 Android／iOS／硬體安全金鑰裝置。
• 快速啟動
live-server --host=localhost --port=8080，本地直接測試符合 WebAuthn 標準。

⸻

快速開始 Quick Start

# 1. 下載專案

git clone https://github.com/lazyjerry/webauthn-client-demo.git
cd webauthn-client-demo

# 2. 啟動本地伺服器（需 Node ≥14）

npm i -g live-server
live-server --host=localhost --port=8080

瀏覽 http://localhost:8080，即可看到註冊／登入畫面。

⸻

搭配 Server 部署 1. 後端部署
Fork 並參考 lazyjerry/webauthn 部署至 Cloudflare Workers
（需開啟 Workers KV 功能）。 2. 設定前端 API
修改 index.html 頂部：

const API = "https://webauthn.<your-subdomain>.workers.dev";

    3.	重新整理頁面，即可完成無密碼登入／註冊體驗。

⸻

專案結構 Structure

web-authn-client-demo/
├─ index.html # 單頁 DEMO，JS/HTML/CSS 集中管理
├─ utils/
│ └─ challenge.js # (後端用) 安全隨機 challenge 產生器
├─ docs/
│ └─ screenshot.png
└─ README.md

⸻

技術棧 Tech Stack

分類 使用套件 說明
WebAuthn 客戶端 @passwordless-id/webauthn (v2.3.0) 使用 jsDelivr +esm 載入
UI 框架 TailwindCSS CDN 版 輕量快速的樣式設計
圖示 Font Awesome 6 指紋／金鑰圖示支援
本地伺服器 live-server 簡單即時重載伺服器

⸻

常見問題 FAQ

問題 解法
SecurityError: This is an invalid domain. 請使用 localhost 或部署 HTTPS 網域，不可使用 127.0.0.1。
Provided challenge is not properly encoded in Base64url Server 端請使用 base64url 格式產生 challenge。
Unexpected authenticator counter: 0 已在後端自動跳過 counter 驗證（v2.3.0 改善版 Worker）。

⸻

授權 License

本專案採用 MIT License。
歡迎自由使用、修改、散佈，請保留原始授權聲明。

⸻

快速上手 WebAuthn，打造無密碼未來！🚀

---

✅ 前端 demo 連結  
✅ 後端 demo 說明（可能失效＋引導去 GitHub）  
✅ 強調新版 webauthn sdk 與 module 化  
✅ 保持專業又好懂的格式
