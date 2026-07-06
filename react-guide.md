# React 完整使用指南

## 目錄
- [基礎知識](#基礎知識)
- [環境準備](#環境準備)
- [專案建立](#專案建立)
- [核心概念](#核心概念)
- [常用工具與指令](#常用工具與指令)
- [除錯與測試](#除錯與測試)
- [最佳實踐](#最佳實踐)

## 基礎知識

### 什麼是 React？
React 是用於建立使用者介面的 JavaScript 函式庫，核心特色：
1. 元件化開發
2. 宣告式 UI
3. 單向資料流
4. 生態系完整（Router、State、Testing）

## 環境準備

- Node.js 18+
- npm 或 yarn
- VS Code（選用）

```bash
node --version
npm --version
```

## 專案建立

```bash
# 使用 Vite 建立 React 專案（建議）
npm create vite@latest my-react-app -- --template react
cd my-react-app
npm install
npm run dev
```

## 核心概念

### 1. 元件與 Props
- 將 UI 拆成可重用元件
- 使用 props 傳遞資料

### 2. State 與事件
- `useState` 管理局部狀態
- 透過事件處理函式更新資料

### 3. Effects
- `useEffect` 處理 API 呼叫、訂閱與清理

### 4. 路由
- 使用 `react-router-dom` 進行頁面切換

## 常用工具與指令

```bash
# 安裝常用依賴
npm install react-router-dom axios

# 執行檢查
npm run lint

# 打包
npm run build
```

## 除錯與測試

```bash
# 安裝測試工具
npm install -D vitest @testing-library/react @testing-library/jest-dom

# 執行測試
npm run test
```

## 最佳實踐

1. 元件職責單一、避免過度耦合
2. 共享狀態優先使用 Context 或狀態管理工具
3. 將 API 呼叫集中到 service 層
4. 維持一致命名規則與資料夾結構
5. 對關鍵互動撰寫測試
