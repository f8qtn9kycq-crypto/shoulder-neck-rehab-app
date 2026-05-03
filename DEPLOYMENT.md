# 肩頸復健中心 - GitHub Pages 部署指南

## 🚀 快速開始 (5 分鐘)

### Step 1: 建立 GitHub Repository

1. 前往 [github.com/new](https://github.com/new)
2. 名稱：`rehab-app` (或任何你喜歡的名稱)
3. 描述：「Shoulder & Neck Rehabilitation Guide with Video Tutorials」
4. 選擇 **Public** (允許他人存取你的應用)
5. 點擊 **Create repository**

### Step 2: 上傳檔案

**使用網頁界面 (最簡單)：**

1. 在你的新 repository 頁面，點擊 **Add file** → **Upload files**
2. 拖放或選擇這些檔案：
   - `index.html`
   - `.gitignore` (下面有提供)
   - `README.md` (下面有提供)
3. 在 commit message 欄輸入：`Initial commit: Add rehab app`
4. 點擊 **Commit changes**

**使用 Git 命令行 (進階)：**

```bash
# 1. Clone repository
git clone https://github.com/YOUR_USERNAME/rehab-app.git
cd rehab-app

# 2. 複製 index.html 到資料夾
cp index.html .

# 3. Commit 並推送
git add index.html
git commit -m "Initial commit: Add rehab app"
git branch -M main
git push -u origin main
```

### Step 3: 啟用 GitHub Pages

1. 進入 Repository → **Settings**
2. 左側選單 → **Pages**
3. **Source** 選擇 **Deploy from a branch**
4. **Branch** 選擇 **main** 和 **/(root)**
5. 點擊 **Save**
6. 等待 1-2 分鐘後，你會看到：
   ```
   Your site is live at https://YOUR_USERNAME.github.io/rehab-app
   ```

✅ **完成！** 你的應用現在在線上了。

---

## 📱 行動優化檢查清單

這個版本已包括所有修復：

- ✅ **效能優化**
  - 內聯 CSS（無 Tailwind CDN）
  - 延遲載入 Chart.js（只在需要時）
  - 使用系統字體堆棧（更快載入）
  - ~45KB 總大小（可在 3G 上運行）

- ✅ **行動 UI**
  - 響應式設計（適應所有螢幕大小）
  - 觸控友善按鈕（≥44×44px 最小觸控目標）
  - 固定標題導航
  - 行動端優先設計

- ✅ **無障礙**
  - 鍵盤導航（Tab、Escape）
  - 焦點指示器（所有互動元素）
  - 語義 HTML
  - 文字對比度 WCAG AA

- ✅ **影片播放**
  - YouTube 搜尋連結（開啟新分頁）
  - 支援所有行動裝置
  - 無沙箱限制

---

## 🎯 新增功能後的部署

### 方法 A：使用網頁界面 (推薦新手)

1. 前往 GitHub repository
2. 點擊檔案名稱（例如 `index.html`）
3. 點擊編輯圖示（鉛筆 ✏️）
4. 進行更改
5. 點擊 **Commit changes...**
6. 輸入 commit message
7. 選 **Commit directly to main branch**
8. 等待 30 秒 → 網站自動更新

### 方法 B：使用命令行 (推薦進階使用者)

```bash
# 1. 編輯 index.html（使用你的編輯器）
# 2. 檢查更改
git status

# 3. Commit
git add index.html
git commit -m "描述你的變更"

# 4. 推送到 GitHub
git push origin main

# 5. 完成！GitHub Pages 會自動重新發布（1-2 分鐘）
```

---

## 🔧 自訂網域名稱（可選）

如果你想用自己的網域（例如 `myrehab.com`）：

1. Repository **Settings** → **Pages**
2. **Custom domain** 欄位輸入你的網域
3. 按照 GitHub 的說明更新 DNS 設定（通常在你的網域商那裡）
4. 勾選 **Enforce HTTPS**

---

## 📊 監控應用程式

### 檢查部署狀態

1. Repository → **Actions** 標籤
2. 你會看到部署工作流程的歷史
3. ✅ 綠色勾號 = 部署成功
4. ❌ 紅色 X = 有錯誤（檢查日誌）

### 檢查網站是否上線

- 開啟瀏覽器 → `https://YOUR_USERNAME.github.io/rehab-app`
- 在手機上測試
- 檢查主控台是否有錯誤 (F12 → Console)

---

## 🔄 應用更新與版本控制

每次進行重要更新時，建議在 HTML 開頭加入版本號：

```html
<!-- 2025-05-03: v1.2.0 - Added Escape key modal close, fixed scroll lock -->
```

這樣其他貢獻者可以追蹤變更。

---

## 🐛 常見問題

### Q: 網站顯示 404？
**A:** 檢查設定：Repository → Settings → Pages → Source 是否設為 `main` 分支

### Q: 更改沒有顯示？
**A:** 
1. 等待 1-2 分鐘（GitHub Pages 需要時間重新發布）
2. 硬重新整理瀏覽器 (Ctrl+Shift+R 或 Cmd+Shift+R)
3. 檢查 Actions 標籤看部署是否成功

### Q: 影片不會播放？
**A:** 這是預期行為 - 應用提供 YouTube 搜尋連結，點擊會開啟新視窗。這避免了嵌入的 iframe 沙箱問題。

### Q: 如何備份我的更改？
**A:** Git 自動備份你的所有提交。使用 `git log` 檢視歷史。

---

## 📈 效能優化建議

### 圖片（如果你想加入）
```html
<!-- 使用 WebP 格式，並有 PNG 備份 -->
<picture>
  <source srcset="demo.webp" type="image/webp">
  <img src="demo.png" alt="運動演示" loading="lazy">
</picture>
```

### 監控載入時間
1. 開啟 DevTools (F12)
2. **Network** 標籤
3. 刷新頁面
4. 查看傳輸大小與載入時間

目標：< 2 秒在 4G、< 5 秒在 3G

---

## 🌍 全球可用性

你的應用透過 GitHub Pages 在全球託管：
- 自動 CDN（所有用戶都能快速載入）
- HTTPS（已內建安全性）
- 無需伺服器維護
- 免費！

---

## 📞 支援與回饋

要報告問題或建議新功能，請在 GitHub Issues 開啟票券。

---

## 📝 預設許可證

建議在 GitHub repository 上加入 MIT License，讓其他物理治療師可以使用或修改你的應用。

在 repository 頁面點擊 **Add file** → **Create new file** → 名稱 `LICENSE`，選擇範本 MIT License。

---

## 🎓 下一步

現在你的應用上線了，考慮：

1. **新增更多練習** - 編輯 `exercises` 陣列
2. **自訂顏色** - 修改 CSS `:root` 變數
3. **蒐集用戶回饋** - 新增簡單的反饋表單
4. **進階功能** - 新增進度追蹤（需要後端）

---

**祝賀！** 🎉 你已成功部署一個專業的復健教學應用程式。
