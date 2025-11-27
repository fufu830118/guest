# 🪐 Wiwynn 訪客管理系統

智慧化訪客登記與數據分析平台，結合 Three.js 九大行星動畫與 Chart.js 數據視覺化。

## ✨ 功能特色

### 📝 訪客登記系統
- 🪐 **九大行星主題背景** - 使用真實行星紋理的 3D 動畫
- ⭐ **閃爍星空效果** - 3000+ 顆動態星星
- 📸 **照片拍攝** - 支持相機拍照
- ✍️ **電子簽名** - Canvas 手寫簽名
- 👥 **員工搜尋** - 快速找到拜訪對象
- 📋 **規章同意** - 訪客規章確認

### 📊 數據儀表板
- 📈 **即時統計** - 今日訪客、在場人數、平均時長
- 🎯 **6種圖表** - 折線圖、柱狀圖、圓餅圖、雷達圖
- 🔄 **自動更新** - 每30秒刷新模擬數據
- 🌟 **星空背景** - 與登記頁面一致的視覺體驗
- 📱 **響應式設計** - 完美支持手機、平板、桌面

## 🚀 技術棧

- **前端框架**: 純 HTML5 + CSS3 + JavaScript (ES6+)
- **3D 渲染**: Three.js (r160)
- **圖表庫**: Chart.js
- **字體**: Google Fonts - Inter
- **設計**: Glassmorphism 玻璃擬態風格

## 📂 文件結構

```
訪客系統/
├── index.html                    # 首頁導航
├── visitor-register.html         # 訪客登記頁面
├── dashboard.html                # 數據儀表板
├── three.min.js                  # Three.js 庫
├── chart.min.js                  # Chart.js 庫
├── Wiwynn_LOGO_with Chinese_Name_Blue_Green (2).png  # Logo
└── person-main/                  # 行星紋理資源
    └── textures/
        ├── 2k_sun.jpg
        ├── 2k_mercury.jpg
        ├── 2k_venus_surface.jpg
        ├── 2k_earth_daymap.jpg
        ├── 2k_mars.jpg
        ├── 2k_jupiter.jpg
        ├── 2k_saturn.jpg
        ├── 2k_saturn_ring_alpha.png
        ├── 2k_uranus.jpg
        ├── 2k_neptune.jpg
        └── 2k_moon.jpg
```

## 🎨 設計亮點

### 視覺效果
- **玻璃擬態** - 半透明背景 + 模糊效果
- **霓虹發光** - Cyan 主題色 (#00f2ff)
- **平滑動畫** - CSS + Three.js 結合
- **星空閃爍** - 正弦波動態大小變化

### 交互體驗
- **拖拽旋轉** - 九大行星場景可旋轉查看
- **懸停效果** - 按鈕、卡片互動反饋
- **表單驗證** - 即時錯誤提示
- **響應式布局** - 自適應各種屏幕

## 🌟 特色功能

### 九大行星動畫
- ☀️ 太陽：脈動發光效果
- 🌍 地球：雲層動畫
- 🪐 土星：半透明光環
- ⭐ 軌道：發光軌道線
- 🌟 星空：3000+ 閃爍星星

### 數據視覺化
- 📊 訪客流量 24 小時趨勢
- 📈 各部門訪問量 3D 柱狀圖
- 🥧 訪客類型分布圓餅圖
- 🕸️ 高峰時段雷達圖
- 📉 每週趨勢多折線圖
- 📊 訪問目的橫向柱狀圖

## 🔧 部署說明

### GitHub Pages 部署

1. **創建 GitHub 倉庫**
```bash
git init
git add .
git commit -m "🚀 Initial commit: Wiwynn Visitor System"
```

2. **推送到 GitHub**
```bash
git remote add origin https://github.com/你的用戶名/wiwynn-visitor-system.git
git branch -M main
git push -u origin main
```

3. **啟用 GitHub Pages**
- 進入倉庫 Settings → Pages
- Source 選擇 `main` 分支
- 點擊 Save

4. **訪問網站**
```
https://你的用戶名.github.io/wiwynn-visitor-system/
```

## 📱 瀏覽器支持

- ✅ Chrome / Edge (推薦)
- ✅ Firefox
- ✅ Safari
- ✅ 移動端瀏覽器

## 📝 License

MIT License - 僅供展示和學習使用

## 👨‍💻 作者

Made with ❤️ by Wiwynn Team

---

⭐ 如果這個項目對您有幫助，請給一個星星！
