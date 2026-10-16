# gh/dash · 多專案管理台

在手機上管理所有 GitHub repo：瀏覽檔案、看 commit、上傳檔案、建立或刪除 repo、開啟 Pages。

**線上使用**：https://kftseng2oo1.github.io/gh/

## 主要功能
- Repo 列表：排序、搜尋、多選批次操作
- Repo 詳情：最近 commits、檔案樹、檔案預覽與下載、README 摘要與技術偵測
- 拖曳上傳檔案並 commit，可一次 commit 到多個 repo
- 建立新 repo（可套用範本）、刪除 repo、一鍵開啟 GitHub Pages
- 顯示 API 剩餘額度
- 設定時會做連線診斷，指出 Worker 網址拼錯、密鑰不符、Token 過期等問題

## 設定
需要自己部署一個 Cloudflare Worker 當代理（例如 `github-manager.<你的子網域>.workers.dev`），環境變數：
- `GITHUB_TOKEN`：GitHub Personal Access Token
- `DASH_SECRET`：自訂密鑰，App 設定裡填一樣的值

App 內「⚙ 設定」填入 Worker URL（結尾不要斜線）、Owner、密鑰。

## 技術與依賴
- 單檔 HTML PWA（`index.html` 內含全部 HTML/CSS/JS），`manifest.json` + `sw.js` 提供安裝到主畫面與離線快取。
- 所有 GitHub API 呼叫經過自架 Worker，Token 不放在前端
