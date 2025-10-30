[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/yOwut1-r)
[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=21349764&assignment_repo_type=AssignmentRepo)

# 🧠 MIL Terms Explorer - Neurosynth Frontend

一個美觀、易用的神經科學研究詞彙瀏覽器，用於查詢和探索 Neurosynth API 的資料。

![Version](https://img.shields.io/badge/version-1.0.0-blue)
![License](https://img.shields.io/badge/license-MIT-green)

## 📋 目錄

- [功能特色](#功能特色)
- [快速開始](#快速開始)
- [API 端點說明](#api-端點說明)
- [使用指南](#使用指南)
- [技術架構](#技術架構)
- [瀏覽器支援](#瀏覽器支援)
- [授權條款](#授權條款)

## ✨ 功能特色

### 1️⃣ `/terms` - 所有可用詞彙
- 📊 以美觀的卡片網格方式呈現所有神經科學相關詞彙
- 🎨 響應式設計，自動適應不同螢幕大小（手機 2 欄、平板 3-4 欄、電腦 5-6 欄）
- 📋 點擊任何詞彙即可複製到剪貼簿
- ⚡ 自動載入，無需手動操作

### 2️⃣ `/terms/<t1>` - 關聯詞彙查詢
- 🔍 查詢與特定詞彙相關的其他詞彙
- 📈 顯示 Jaccard 相似度係數（精確到小數點後 4 位）
- 🔢 顯示共現次數 (co_count)
- 💳 大型資訊卡片設計，易於閱讀和比較

### 3️⃣ `/query/<q_string>/studies` - 邏輯搜尋研究
- 🎯 支援邏輯運算子：`AND`、`OR`、`NOT`
- 📚 顯示完整的研究資訊：
  - 論文標題
  - 作者列表
  - 期刊名稱
  - 發表年份
  - Study ID 和 Contrast ID
- 📊 顯示總結果數量和已套用的過濾器
- 🎴 卡片式佈局，清晰呈現每筆研究資料

## 🚀 快速開始

### 方法一：直接開啟（最簡單）

1. 下載專案檔案
2. 直接在瀏覽器中開啟 `index.html`
3. 開始使用！

### 方法二：使用本地伺服器（推薦）

```bash
# 使用 Python 3
cd /path/to/neurosynth-frontend-mikashih-main
python3 -m http.server 8000

# 或使用 Python 2
python -m SimpleHTTPServer 8000

# 或使用 Node.js
npx serve

# 或使用 PHP
php -S localhost:8000
```

然後在瀏覽器中開啟：`http://localhost:8000`

## 🔌 API 端點說明

### API Base URL
預設：`https://mil.psy.ntu.edu.tw:5000`

可在網頁右上角的輸入框中自訂 API 伺服器位址。

### 端點詳情

#### 1. GET `/terms`
獲取所有可用的神經科學詞彙。

**回傳格式：**
```json
{
  "terms": ["aberrant", "abilities", "ability", "able", "abnormal", ...]
}
```

#### 2. GET `/terms/<t1>`
獲取與指定詞彙相關的其他詞彙。

**範例：** `/terms/posterior_cingulate`

**回傳格式：**
```json
{
  "related": [
    {
      "term": "emotional",
      "co_count": 726,
      "jaccard": 0.2834830144474815
    },
    {
      "term": "emotion",
      "co_count": 499,
      "jaccard": 0.23571091166745395
    }
  ]
}
```

#### 3. GET `/query/<q_string>/studies`
使用邏輯查詢字串搜尋相關研究。

**範例：** `/query/posterior_cingulate AND NOT ventromedial_prefrontal/studies`

**回傳格式：**
```json
{
  "applied": {
    "locations": false,
    "r": null,
    "terms": true
  },
  "count": 292,
  "results": [
    {
      "id": "10594068-1",
      "study_id": "10594068",
      "contrast_id": "1",
      "title": "Amygdala-hippocampal involvement in human aversive trace conditioning...",
      "authors": "Buchel C, Dolan RJ, Armony JL, Friston KJ",
      "journal": "The Journal of neuroscience...",
      "year": 1999
    }
  ]
}
```

## 📖 使用指南

### 查詢所有詞彙
1. 點擊「/terms」標籤（預設已選中）
2. 頁面會自動載入所有可用詞彙
3. 點擊任何詞彙卡片即可複製到剪貼簿
4. 點擊「🔄 重新載入」按鈕可手動重新載入

### 查詢關聯詞彙
1. 點擊「/terms/<t1>」標籤
2. 在輸入框中輸入想查詢的詞彙，例如：
   - `posterior_cingulate`
   - `emotional`
   - `hippocampus`
3. 點擊「查詢」按鈕
4. 查看與該詞彙相關的其他詞彙，包含相似度分數

### 邏輯搜尋研究
1. 點擊「/query/<q_string>/studies」標籤
2. 輸入查詢字串，支援以下語法：
   - **單一詞彙：** `posterior_cingulate`
   - **AND 運算：** `posterior_cingulate AND emotional`
   - **OR 運算：** `emotional OR emotion`
   - **NOT 運算：** `posterior_cingulate AND NOT ventromedial_prefrontal`
   - **組合運算：** `(emotional OR emotion) AND NOT negative`
3. 點擊「查詢」按鈕
4. 瀏覽符合條件的研究結果

## 🛠️ 技術架構

### 前端技術
- **HTML5**：語義化標記
- **Tailwind CSS**：透過 CDN 引入，無需安裝
- **原生 JavaScript (ES6+)**：
  - Fetch API 進行非同步資料請求
  - 現代化的 async/await 語法
  - DOM 操作和事件處理

### 設計特色
- 📱 **完全響應式**：自適應手機、平板、桌面螢幕
- 🎨 **現代化 UI**：漸層色彩、流暢動畫、陰影效果
- ♿ **易用性**：直覺的操作介面、清晰的狀態提示
- 🚀 **零依賴**：無需 npm install，開箱即用
- 🔄 **即時反饋**：載入狀態、錯誤提示、成功確認

### 檔案結構
```
neurosynth-frontend-mikashih-main/
├── index.html          # 主要應用程式（包含 HTML、CSS、JavaScript）
├── README.md           # 專案說明文件
└── LICENSE            # 授權條款
```

**注意事項：**
- 需要支援 ES6+ 語法（async/await、箭頭函式等）
- 需要支援 Fetch API
- 需要支援 Clipboard API（複製功能）
- 建議使用最新版本的瀏覽器以獲得最佳體驗
