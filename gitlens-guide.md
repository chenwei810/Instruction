# GitLens 完整使用指南

## 目錄
- [安裝與設定](#安裝與設定)
- [基本功能](#基本功能)
- [進階功能](#進階功能)
- [常用設定](#常用設定)
- [快捷鍵](#快捷鍵)
- [實用技巧](#實用技巧)

## 安裝與設定

### 安裝步驟

1. 打開 VS Code
2. 點擊左側擴充功能圖示（Extensions）
3. 搜尋 "GitLens"
4. 點擊 "Install" 安裝
5. 安裝完成後重新啟動 VS Code

### 初始設定

1. 在 VS Code 中打開命令面板（Command Palette）
   - Windows/Linux: `Ctrl + Shift + P`
   - Mac: `Cmd + Shift + P`
2. 輸入 "GitLens: Open Settings"
3. 選擇您想要的設定模式：
   - **簡單模式**：基本功能
   - **進階模式**：完整功能

## 基本功能

### 1. 行內 Blame 資訊
- 顯示每一行程式碼的最後修改者和時間
- 將滑鼠移到行內 blame 資訊上可以看到詳細的 commit 訊息

### 2. 程式碼鏡頭（CodeLens）
```
// 在函數或類別上方顯示最後修改資訊
function example() {
    // 程式碼...
}
```

### 3. 目前行詳細資訊
- 顯示目前游標所在行的詳細修改歷史
- 包含作者、日期、commit 訊息等

### 4. 檔案歷史記錄
- 查看檔案的完整修改歷史
- 比較不同版本的變更

## 進階功能

### 1. 儲存庫視圖

在左側面板中可以看到：
- **檔案歷史記錄**
- **行歷史記錄**
- **搜尋 Commits**
- **比較視圖**
- **儲存庫狀態**

### 2. 視覺化比較

```
# 支援多種比較模式
- 工作區 vs 暫存區
- 暫存區 vs HEAD
- 分支間比較
- 標籤間比較
```

### 3. Heat Map
- 顯示檔案修改頻率
- 識別經常變更的程式碼區域

### 4. 互動式補綴（Interactive Rebase）
- 視覺化方式重新排序 commits
- 修改、合併或刪除 commits

## 常用設定

### 1. 行內 Blame 設定
```json
{
    "gitlens.currentLine.enabled": true,
    "gitlens.currentLine.scrollable": false,
    "gitlens.currentLine.format": "${author}, ${date} • ${message}"
}
```

### 2. CodeLens 設定
```json
{
    "gitlens.codeLens.enabled": true,
    "gitlens.codeLens.authors.enabled": true,
    "gitlens.codeLens.recentChange.enabled": true
}
```

### 3. 視圖設定
```json
{
    "gitlens.views.repositories.location": "scm",
    "gitlens.views.fileHistory.location": "explorer",
    "gitlens.views.lineHistory.location": "explorer"
}
```

## 快捷鍵

### 基本操作
- `Alt + B`：開啟/關閉行內 blame
- `Alt + H`：查看檔案歷史記錄
- `Alt + L`：查看行歷史記錄
- `Ctrl/Cmd + Shift + G`：開啟 Git 面板

### 進階操作
- `Ctrl/Cmd + Shift + G, H`：開啟儲存庫歷史記錄
- `Ctrl/Cmd + Shift + G, S`：開啟搜尋 commits
- `Ctrl/Cmd + Shift + G, C`：開啟比較視圖

## 實用技巧

### 1. 快速查看變更

1. 使用行內 blame 查看最後修改：
   - 將滑鼠移到行號旁邊
   - 點擊顯示的 commit 資訊

2. 比較變更：
   - 在檔案歷史中選擇兩個版本
   - 右鍵選擇「Compare」

### 2. 搜尋技巧

```
# 搜尋特定作者的修改
author:name

# 搜尋特定時間範圍
before:2023-01-01
after:2022-01-01

# 搜尋特定訊息
message:"bug fix"
```

### 3. 分支管理

1. 在儲存庫視圖中：
   - 查看所有分支
   - 比較分支差異
   - 合併分支
   - 重新命名分支

2. 使用視覺化工具：
   - 查看分支圖
   - 追蹤分支關係
   - 管理遠端分支

### 4. 檢視歷史

1. **並排比較**：
   - 選擇兩個版本
   - 使用並排視圖比較差異

2. **行歷史追蹤**：
   - 選擇特定程式碼行
   - 查看該行的完整修改歷史

## 進階應用

### 1. 工作流程整合

1. **程式碼審查**：
   - 使用比較視圖檢查變更
   - 添加行內註解
   - 追蹤修改歷史

2. **問題追蹤**：
   - 連結 commits 與 issues
   - 查看相關變更
   - 追蹤問題解決進度

### 2. 自訂設定

```json
{
    // 自訂提交訊息格式
    "gitlens.advanced.messages": {
        "commit": "${message} (${author})",
        "commit_details": "${message}\n\n${author} (${email})\n${date}"
    },
    
    // 自訂日期格式
    "gitlens.advanced.dateFormat": "YYYY-MM-DD HH:mm:ss",
    
    // 自訂快捷鍵
    "gitlens.keymap": "alternate"
}
```

## 常見問題解決

### 1. 效能問題

如果 GitLens 運行緩慢：
1. 關閉不必要的功能
2. 調整更新頻率
3. 限制歷史記錄深度

### 2. 顯示問題

如果資訊顯示不正確：
1. 重新載入視窗
2. 更新 Git 設定
3. 檢查檔案編碼

### 3. 整合問題

如果與其他擴充功能衝突：
1. 檢查相容性
2. 調整優先順序
3. 更新擴充功能

## 最佳實踐建議

1. **適度使用**
   - 根據需求開啟功能
   - 避免開啟過多視圖

2. **保持更新**
   - 定期更新 GitLens
   - 追蹤新功能公告

3. **團隊協作**
   - 統一設定檔
   - 建立共同工作流程

## 學習資源

- [GitLens 官方文件](https://gitlens.amod.io/)
- [VS Code GitLens 文件](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens)
- [GitLens 影片教學](https://www.youtube.com/results?search_query=gitlens+tutorial)

記住，GitLens 是一個功能強大的工具，建議從基本功能開始使用，逐步探索更進階的功能。根據您的工作流程和需求，調整合適的設定。
