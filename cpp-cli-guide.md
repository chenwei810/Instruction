# C++ 命令列編譯與執行指南

## 目錄
- [基本環境設置](#基本環境設置)
- [Windows 系統](#windows-系統)
- [Mac/Linux 系統](#maclinux-系統)
- [編譯與執行](#編譯與執行)
- [常見錯誤處理](#常見錯誤處理)
- [進階編譯選項](#進階編譯選項)
- [實用技巧](#實用技巧)

## 基本環境設置

### 必要工具

1. **編譯器**
   - Windows: MinGW (gcc/g++)
   - Mac: Xcode Command Line Tools (clang++)
   - Linux: gcc/g++

2. **文字編輯器** (選擇其一)
   - Visual Studio Code
   - Sublime Text
   - Notepad++
   - Vim/Nano

### 環境變數設置

#### Windows
1. 右鍵點擊「本機」→ 內容 → 進階系統設定 → 環境變數
2. 在「系統變數」中找到 Path
3. 新增 MinGW 的 bin 目錄路徑（例如：`C:\MinGW\bin`）

#### Mac/Linux
通常不需要額外設置，安裝完編譯器後即可使用

## Windows 系統

### 安裝 MinGW

1. 下載 MinGW 安裝程式
   - 前往 [MinGW 官網](https://mingw-w64.org/)
   - 或使用 [MSYS2](https://www.msys2.org/)

2. 安裝步驟
```bash
# 使用 MSYS2 安裝 (推薦)
pacman -S mingw-w64-x86_64-gcc
pacman -S mingw-w64-x86_64-toolchain
```

### 基本命令

```bat
# 切換目錄
cd 目標路徑

# 列出目錄內容
dir

# 清除螢幕
cls
```

## Mac/Linux 系統

### 安裝編譯器

#### Mac
```bash
# 安裝 Xcode Command Line Tools
xcode-select --install
```

#### Linux (Ubuntu/Debian)
```bash
# 安裝 g++
sudo apt update
sudo apt install g++
```

### 基本命令

```bash
# 切換目錄
cd 目標路徑

# 列出目錄內容
ls

# 清除螢幕
clear
```

## 編譯與執行

### 基本編譯

```bash
# 單檔編譯
g++ program.cpp -o program

# 執行程式
# Windows
program.exe

# Mac/Linux
./program
```

### 多檔案編譯

```bash
# 編譯多個源文件
g++ main.cpp functions.cpp -o program

# 使用萬用字元
g++ *.cpp -o program
```

### 編譯過程展示

1. 創建源文件：`hello.cpp`
```cpp
#include <iostream>

int main() {
    std::cout << "Hello, World!" << std::endl;
    return 0;
}
```

2. 編譯指令
```bash
# 基本編譯
g++ hello.cpp -o hello

# 或指定 C++ 版本
g++ -std=c++11 hello.cpp -o hello
```

3. 執行程式
```bash
# Windows
hello.exe

# Mac/Linux
./hello
```

## 常見錯誤處理

### 1. 找不到編譯器

```bash
# Windows：確認 PATH
echo %PATH%

# Mac/Linux：確認編譯器位置
which g++
```

### 2. 編譯錯誤

```bash
# 顯示詳細錯誤訊息
g++ -Wall program.cpp -o program

# 顯示所有警告
g++ -Wall -Wextra program.cpp -o program
```

### 3. 執行權限問題 (Mac/Linux)

```bash
# 添加執行權限
chmod +x program
```

## 進階編譯選項

### 優化選項

```bash
# 基本優化
g++ -O2 program.cpp -o program

# 最高優化
g++ -O3 program.cpp -o program

# 調試版本
g++ -g program.cpp -o program
```

### 標準選擇

```bash
# C++11
g++ -std=c++11 program.cpp -o program

# C++14
g++ -std=c++14 program.cpp -o program

# C++17
g++ -std=c++17 program.cpp -o program

# C++20
g++ -std=c++20 program.cpp -o program
```

### 其他有用選項

```bash
# 生成依賴文件
g++ -MM program.cpp

# 只編譯不鏈接
g++ -c program.cpp

# 包含調試信息
g++ -g program.cpp -o program
```

## 實用技巧

### 1. 批次編譯腳本

#### Windows (batch)
```batch
@echo off
g++ -std=c++11 *.cpp -o program
if %errorlevel% equ 0 (
    echo 編譯成功！
    program.exe
) else (
    echo 編譯失敗！
)
pause
```

#### Mac/Linux (shell)
```bash
#!/bin/bash
g++ -std=c++11 *.cpp -o program
if [ $? -eq 0 ]; then
    echo "編譯成功！"
    ./program
else
    echo "編譯失敗！"
fi
```

### 2. 常用編譯標記組合

```bash
# 開發版本（包含調試信息和警告）
g++ -g -Wall -Wextra program.cpp -o program

# 發布版本（優化）
g++ -O2 -DNDEBUG program.cpp -o program
```

### 3. Makefile 基本使用

```makefile
CXX = g++
CXXFLAGS = -std=c++11 -Wall

program: main.cpp functions.cpp
    $(CXX) $(CXXFLAGS) main.cpp functions.cpp -o program

clean:
    rm -f program *.o
```

## 建議實踐

1. **組織專案結構**
```
project/
│
├── src/
│   ├── main.cpp
│   └── functions.cpp
│
├── include/
│   └── functions.h
│
└── build/
```

2. **使用版本控制**
- 創建 `.gitignore`
```
*.exe
*.o
build/
```

3. **善用編譯標記**
- 開發時使用 `-Wall -Wextra`
- 發布時使用 `-O2 -DNDEBUG`

## 學習資源

- [CPP Reference](https://en.cppreference.com/)
- [GCC 官方文檔](https://gcc.gnu.org/onlinedocs/)
- [C++ Compiler Explorer](https://godbolt.org/)

## 常見問題整理

1. **找不到標頭檔**
```bash
# 添加包含目錄
g++ -I./include program.cpp -o program
```

2. **鏈接錯誤**
```bash
# 添加鏈接庫
g++ program.cpp -lmath -o program
```

3. **中文編碼問題**
```bash
# Windows 使用 GBK 編碼
g++ -fexec-charset=GBK program.cpp -o program
```

記住，命令列操作需要練習才能熟練。建議從簡單的程式開始，逐步嘗試更複雜的編譯選項和專案結構。
