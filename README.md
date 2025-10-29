[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/yOwut1-r)
[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=21349764&assignment_repo_type=AssignmentRepo)

# 🧠 Neurosynth Frontend

使用 AJAX 和 Tailwind CSS 建立的 Neurosynth 術語查詢前端介面。

## ✨ 功能特色

- 🎨 使用 Tailwind CSS 打造的現代化 UI
- 🔄 AJAX 技術即時獲取 Neurosynth API 資料
- 📊 詳細的 HTTP 狀態顯示
- 📋 一鍵複製結果
- ⚡ 回應時間統計
- 🎯 友善的錯誤處理

## 🚀 線上展示

專案已部署至 GitHub Pages：
**https://ntu-info.github.io/neurosynth-frontend-mikashih/**

## 💻 本地開發

### 安裝依賴

```bash
npm install
```

### 啟動開發伺服器

```bash
npm run dev
```

專案將在 http://localhost:3000 運行

### 建置生產版本

```bash
npm run build
```

### 預覽生產版本

```bash
npm run preview
```

## 📁 專案結構

```
neurosynth-frontend-mikashih/
├── .github/
│   └── workflows/
│       └── deploy.yml      # GitHub Pages 自動部署
├── index.html              # 主頁面
├── main.css               # Tailwind CSS 設定
├── vite.config.js         # Vite 配置
├── package.json           # 專案依賴
└── README.md             # 專案說明
```

## 🛠️ 技術棧

- **前端框架**: Vanilla JavaScript
- **樣式**: Tailwind CSS 4.x
- **建置工具**: Vite 6.x
- **部署**: GitHub Pages (透過 GitHub Actions)

## 📝 API 說明

專案從以下 API 獲取資料：
```
https://hpc.psy.ntu.edu.tw:5000/terms
```

## 🔧 GitHub Pages 設定

專案已配置自動部署至 GitHub Pages。每次推送到 `main` 分支時，GitHub Actions 會自動建置並部署專案。

### 首次啟用 GitHub Pages

1. 前往 GitHub 倉庫設定
2. 點選左側的 **Pages**
3. 在 **Source** 下選擇 **GitHub Actions**
4. 推送代碼後，GitHub Actions 會自動開始部署

## 📄 授權

本專案使用的授權請參考 LICENSE 檔案。

## 👨‍💻 作者

mikashih
