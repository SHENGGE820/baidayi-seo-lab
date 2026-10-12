# 百達醫 SEO 文章工作室

透過 Gemini 將主題與公司資料整理成候選標題、文章架構與完整 SEO 文章草稿。

公司定位、服務、讀者、語氣及三階段Gemini指令已預設，使用者只需提供本次主題與選填補充資料。[查看公司寫作設定](公司寫作設定說明.md)。管理者可在GitHub維護`company-settings.json`，每次生成都自動帶入，沒有API金鑰存放在設定檔。

**操作網站：https://shengge820.github.io/baidayi-seo-lab/**

這個 GitHub 頁面用來保存原始碼；上方 GitHub Pages 網址才是實際操作入口。

## 操作

1. 到 [Google AI Studio](https://aistudio.google.com/apikey) 建立 Gemini API 金鑰。使用未啟用付費計費的專案；免費額度及模型權限以 Google 專案為準。
2. 開啟操作網站，在上方輸入金鑰並按「測試連接」。不需登入 GPT。
3. 點「載入代工報價範例」，或自行輸入文章主題與參考文字。
4. 依序點「產生標題」→ 選標題 →「用這個標題產生架構」→「產生完整文章」。
5. 檢視草稿，下載文章；也能調整成更精簡、更容易懂或加強詢價引導的版本。

## 換電腦演示

GitHub Pages 可直接開啟，不需要登入網站帳號。每台電腦需要輸入自己的 Gemini 金鑰一次，金鑰不要貼到聊天裡。

也可下載 `index.html`，用 Chrome 或 Edge 直接開啟；即時生成仍需要網路。可下載「實作紀錄」，在另一台電腦載入各步成果；實作紀錄不含金鑰。

## 資料與金鑰

- 原始碼與網站不含 API 金鑰。
- 使用者输入的金鑰只保留在目前頁面的記憶中，直接送到 Google API，不写入 sessionStorage、文章下載或實作紀錄。
- 重新整理或關閉頁面後，金鑰會清除。草稿暫存於本分頁的 sessionStorage。
- 免費服務資料可能用於改善 Google 產品；演示請使用公開資料。
- 這是使用者自行輸入本人金鑰的個人實作工具，沒有內嵌共用金鑰。正式多人服務應另做伺服器保護共用憑證。

## 範圍與驗證

- 不自動讀取網址，参考資料請貼文字或載入文字檔。百達醫公開服務及代工報價資料已內建。
- 關鍵字只是候選方向，沒有搜尋量或排名資料。
- 文章須由公司確認後再發布。本工具沒有連接官網後台、GA 或 Search Console。
- 完成頁提供發布後追蹤成效的說明，沒有虛構流量數據。
- 已以模擬 Google 回覆測試四步流程、標題選擇、文章下載、錯誤時保留草稿、手機版及金鑰不儲存。
- 真實 Gemini 連接與生成需使用者在網頁輸入有效金鑰後驗證。

## 官方資料

- [Gemini API 金鑰](https://ai.google.dev/gemini-api/docs/api-key)
- [模型費用與免費額度](https://ai.google.dev/gemini-api/docs/pricing)
- [百達醫公司網站](https://shengge820.github.io/baidayi-enterprise-website/)
- [全面性服務](https://shengge820.github.io/baidayi-premium-redesign/%E5%85%A8%E9%9D%A2%E6%80%A7%E6%9C%8D%E5%8B%99/index.html)

## 更新網站

網站直接使用 `main` 分支根目錄的 `index.html`，不需要套件或建置。修改後推送到 GitHub，GitHub Pages 會重新部署。

線上版每次開啟會讀取同目錄的`company-settings.json`，載入失敗時會阻擋新生成並提供重試，不會默默使用舊設定。更新可帶走的單一HTML時，執行`node scripts/sync-company-settings.cjs`同步內嵌預設，再提供新檔。
