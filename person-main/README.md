# 王夫楨 - 個人作品集網站

這是一個結合 3D 太陽系場景的個人作品集網站,使用 Three.js 打造沉浸式的互動體驗。

## 🌟 特色

- **3D 太陽系場景**: 使用 Three.js 呈現真實的九大行星與太陽
- **真實行星紋理**: 採用高解析度 2K 行星表面貼圖
- **響應式設計**: 支援桌面與行動裝置
- **深色主題**: 專業的暗色系 UI 設計
- **流暢動畫**: 行星自轉、公轉動畫效果

## 📁 專案結構

```
.
├── index.html          # 主要 HTML 檔案
├── images/             # 圖片資源
│   └── 大頭貼.jpg      # 個人照片
├── textures/           # 3D 紋理貼圖
│   ├── 2k_sun.jpg
│   ├── 2k_mercury.jpg
│   ├── 2k_venus_surface.jpg
│   ├── 2k_earth_daymap.jpg
│   ├── 2k_mars.jpg
│   ├── 2k_jupiter.jpg
│   ├── 2k_saturn.jpg
│   ├── 2k_saturn_ring_alpha.png
│   ├── 2k_uranus.jpg
│   ├── 2k_neptune.jpg
│   └── 2k_moon.jpg
└── README.md           # 專案說明文件
```

## 🚀 部署到 GitHub Pages

### 步驟 1: 建立 GitHub Repository

1. 前往 [GitHub](https://github.com)
2. 點擊右上角的 + → New repository
3. 輸入 repository 名稱 (例如: portfolio)
4. 選擇 Public
5. 點擊 Create repository

### 步驟 2: 上傳檔案

在本地專案資料夾中執行:

```bash
git init
git add .
git commit -m "Initial commit: Portfolio website with 3D solar system"
git branch -M main
git remote add origin https://github.com/你的使用者名稱/portfolio.git
git push -u origin main
```

### 步驟 3: 啟用 GitHub Pages

1. 進入 repository 的 Settings
2. 點擊左側選單的 Pages
3. 在 Source 下拉選單選擇 main 分支
4. 點擊 Save
5. 等待幾分鐘後,網站將會在 https://你的使用者名稱.github.io/portfolio/ 上線

## 🛠️ 技術棧

- **HTML5**: 網頁結構
- **Tailwind CSS**: CSS 框架
- **Three.js**: 3D 圖形渲染
- **JavaScript (ES6+)**: 互動邏輯

## 👨‍💻 關於作者

**王夫楨 (Michael Wang)**
- 📧 Email: f23022340@gmail.com
- 📱 手機: 0953-388-085
- 📍 地點: 台北市中正區
- 🎓 學歷: 國立臺北科技大學 工業工程與管理系

## 📄 授權

此專案僅供個人作品集使用。

## 🙏 致謝

- 行星紋理來源: Solar System Scope
- 3D 引擎: Three.js
- CSS 框架: Tailwind CSS
