# Markdown 完整指南

## 目錄
- [什麼是 Markdown？](#什麼是-markdown)
- [基本語法](#基本語法)
- [進階語法](#進階語法)
- [編輯器推薦](#編輯器推薦)
- [最佳實踐](#最佳實踐)
- [常見問題](#常見問題)

## 什麼是 Markdown？

Markdown 是一種輕量級的標記語言，由 John Gruber 在 2004 年創建。它的設計目標是：
- 易讀易寫
- 純文本格式
- 可轉換為 HTML
- 廣泛應用於文件撰寫、網頁內容、部落格文章等

## 基本語法

### 1. 標題

```markdown
# 一級標題
## 二級標題
### 三級標題
#### 四級標題
##### 五級標題
###### 六級標題
```

### 2. 文字樣式

```markdown
**粗體文字**
*斜體文字*
***粗斜體文字***
~~刪除線~~
`程式碼`
```

顯示效果：
- **粗體文字**
- *斜體文字*
- ***粗斜體文字***
- ~~刪除線~~
- `程式碼`

### 3. 列表

#### 無序列表
```markdown
- 第一項
- 第二項
  - 子項目
  - 子項目
- 第三項
```

#### 有序列表
```markdown
1. 第一項
2. 第二項
   1. 子項目
   2. 子項目
3. 第三項
```

### 4. 連結

```markdown
[顯示文字](網址)
[Google](https://www.google.com)

# 圖片
![替代文字](圖片網址)
```

### 5. 引用

```markdown
> 這是一段引用文字
> 可以有多行
>> 也可以巢狀引用
```

### 6. 分隔線

```markdown
---
或
***
```

## 進階語法

### 1. 表格

```markdown
| 欄位1 | 欄位2 | 欄位3 |
|-------|-------|-------|
| 內容1 | 內容2 | 內容3 |
| 資料1 | 資料2 | 資料3 |
```

### 2. 程式碼區塊

````markdown
```python
def hello():
    print("Hello, World!")
```
````

### 3. 工作清單

```markdown
- [x] 已完成項目
- [ ] 未完成項目
- [ ] 待辦事項
```

### 4. 數學公式（需支援）

```markdown
行內公式：$E = mc^2$

區塊公式：
$$
\sum_{i=1}^n i = \frac{n(n+1)}{2}
$$
```

### 5. 腳註

```markdown
這是一段有腳註[^1]的文字。

[^1]: 這是腳註的內容
```

## 編輯器推薦

### 線上編輯器
1. **StackEdit**
   - 免費、易用
   - 支援即時預覽
   - [網址](https://stackedit.io/)

2. **Dillinger**
   - 簡潔界面
   - 可直接匯出 HTML/PDF
   - [網址](https://dillinger.io/)

### 桌面應用程式
1. **Visual Studio Code**
   - 免費、強大的擴充功能
   - 支援即時預覽
   - 推薦安裝的擴充功能：
     - Markdown All in One
     - Markdown Preview Enhanced

2. **Typora**
   - 所見即所得編輯器
   - 簡潔優雅的界面
   - 支援多種主題

## 最佳實踐

### 1. 文件結構
```markdown
# 文件標題

## 目錄
- [第一部分](#第一部分)
- [第二部分](#第二部分)

## 第一部分
內容...

## 第二部分
內容...
```

### 2. 命名慣例
- 檔案名稱使用小寫
- 單字間用連字符號（-）連接
- 例如：`markdown-guide.md`

### 3. 格式建議
- 標題後空一行
- 使用適當的縮排
- 保持一致的格式風格

### 4. 圖片處理
```markdown
# 本地圖片
![圖片說明](./images/picture.png)

# 線上圖片
![圖片說明](https://example.com/picture.png)
```

## 常見問題

### 1. 換行問題
- 在行尾加兩個空格實現換行
- 或使用空行分隔段落

### 2. 跳脫字元
使用反斜線（\）跳脫特殊字元：
```markdown
\* 這不是斜體 \*
\\ 反斜線
\` 反引號
```

### 3. HTML 支援
Markdown 支援內嵌 HTML：
```markdown
<div style="color: red;">
  這是紅色文字
</div>

<table>
  <tr>
    <td>表格內容</td>
  </tr>
</table>
```

## 進階應用

### 1. 自訂 CSS
某些編輯器支援自訂樣式：
```css
/* style.css */
.markdown-body {
    font-family: "微軟正黑體", sans-serif;
    line-height: 1.6;
}
```

### 2. 快捷鍵
常用的編輯器快捷鍵：
- Ctrl/Cmd + B：粗體
- Ctrl/Cmd + I：斜體
- Ctrl/Cmd + K：插入連結

### 3. 匯出格式
大多數編輯器支援匯出為：
- HTML
- PDF
- Word
- 簡報格式

## 擴充語法

不同平台可能支援額外的語法：

### 1. GitHub Flavored Markdown (GFM)
- 表情符號 :smile:
- 任務清單
- 自動連結
- 表格擴充

### 2. GitLab Markdown
- 數學公式
- 流程圖
- 時序圖

## 實用工具

### 1. 線上轉換工具
- Pandoc：多格式轉換
- PDF 轉換器
- Word 轉 Markdown

### 2. 語法檢查工具
- markdownlint
- Markdown Preview Enhanced

## 學習資源

### 官方資源
- [Markdown 官方文件](https://daringfireball.net/projects/markdown/)
- [GitHub Markdown 指南](https://guides.github.com/features/mastering-markdown/)

### 教學網站
- [Markdown Guide](https://www.markdownguide.org/)
- [CommonMark](https://commonmark.org/)

## 版本控制整合

### Git 相關
- README.md
- CONTRIBUTING.md
- 文件版本控制
- 協作編輯

## 注意事項
1. 保持格式一致性
2. 定期備份文件
3. 適當使用版本控制
4. 注意檔案編碼（建議使用 UTF-8）

---

這份文件使用 Markdown 編寫，您可以將它當作範例參考。建議實際練習每一種語法，以熟悉 Markdown 的使用。
