# Java 開發與執行完整指南

## 目錄
- [環境設置](#環境設置)
- [基本概念](#基本概念)
- [命令列操作](#命令列操作)
- [IDE 使用指南](#ide-使用指南)
- [程式執行](#程式執行)
- [專案管理](#專案管理)
- [除錯技巧](#除錯技巧)
- [常見問題](#常見問題)

## 環境設置

### 1. 安裝 JDK (Java Development Kit)

#### Windows 系統
1. 下載 JDK
   - 前往 [Oracle 官網](https://www.oracle.com/java/technologies/downloads/)
   - 或使用 OpenJDK：[AdoptOpenJDK](https://adoptopenjdk.net/)

2. 安裝步驟
   ```
   1. 執行下載的安裝檔
   2. 選擇安裝路徑（建議使用預設）
   3. 等待安裝完成
   ```

3. 設置環境變數
   ```
   1. 右鍵「本機」→ 內容 → 進階系統設定 → 環境變數
   2. 在「系統變數」中新增：
      JAVA_HOME = C:\Program Files\Java\jdk-版本號
   3. 在 Path 變數中加入：
      %JAVA_HOME%\bin
   ```

#### Mac 系統
```bash
# 使用 Homebrew 安裝
brew install openjdk

# 或下載安裝檔手動安裝
```

#### Linux 系統
```bash
# Ubuntu/Debian
sudo apt update
sudo apt install openjdk-11-jdk

# CentOS/RHEL
sudo yum install java-11-openjdk-devel
```

### 2. 驗證安裝

在命令列輸入：
```bash
# 檢查 Java 版本
java -version

# 檢查 javac 版本
javac -version
```

## 基本概念

### 1. Java 檔案結構

```java
// HelloWorld.java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```

### 2. 編譯與執行過程
```
.java 檔案 → javac 編譯 → .class 檔案 → java 執行
```

## 命令列操作

### 1. 基本指令

```bash
# 編譯 Java 檔案
javac HelloWorld.java

# 執行 Java 程式
java HelloWorld

# 帶參數執行
java HelloWorld arg1 arg2
```

### 2. 編譯選項

```bash
# 指定輸出目錄
javac -d bin HelloWorld.java

# 指定編碼
javac -encoding UTF-8 HelloWorld.java

# 顯示警告
javac -Xlint HelloWorld.java
```

### 3. 執行選項

```bash
# 設定記憶體大小
java -Xmx512m HelloWorld

# 指定類別路徑
java -cp ./bin HelloWorld

# 啟用除錯模式
java -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=5005 HelloWorld
```

## IDE 使用指南

### 1. Eclipse

#### 安裝
1. 下載 Eclipse IDE
2. 執行安裝程式
3. 選擇 Java 開發環境

#### 基本操作
```
1. 建立新專案：File → New → Java Project
2. 建立新類別：右鍵專案 → New → Class
3. 執行程式：右鍵 → Run As → Java Application
```

### 2. IntelliJ IDEA

#### 安裝
1. 下載 IntelliJ IDEA
2. 執行安裝程式
3. 選擇需要的功能

#### 基本操作
```
1. 建立新專案：File → New → Project
2. 建立新類別：右鍵 src → New → Java Class
3. 執行程式：右鍵 → Run
```

### 3. VSCode

#### 安裝
1. 安裝 VSCode
2. 安裝 Java Extension Pack

#### 基本操作
```
1. 建立 Java 檔案
2. 使用命令列或 Run 按鈕執行
3. 使用除錯功能
```

## 程式執行

### 1. 專案結構

```
project/
│
├── src/
│   └── com/example/
│       └── Main.java
│
├── bin/
│   └── com/example/
│       └── Main.class
│
└── lib/
    └── dependencies.jar
```

### 2. 建置與執行

```bash
# 建立目錄
mkdir -p src/com/example
mkdir bin

# 編譯
javac -d bin src/com/example/*.java

# 執行
java -cp bin com.example.Main
```

### 3. 使用外部函式庫

```bash
# 編譯時包含外部 JAR
javac -cp "lib/*" -d bin src/com/example/*.java

# 執行時包含外部 JAR
java -cp "bin:lib/*" com.example.Main
```

## 專案管理

### 1. Maven

#### 安裝 Maven
```bash
# Windows: 下載並設置環境變數
# Mac/Linux
brew install maven  # Mac
sudo apt install maven  # Ubuntu
```

#### 基本使用
```bash
# 創建新專案
mvn archetype:generate

# 編譯專案
mvn compile

# 執行測試
mvn test

# 打包專案
mvn package
```

### 2. Gradle

#### 安裝 Gradle
```bash
# Windows: 下載並設置環境變數
# Mac/Linux
brew install gradle  # Mac
sudo apt install gradle  # Ubuntu
```

#### 基本使用
```bash
# 初始化專案
gradle init

# 編譯專案
gradle build

# 執行程式
gradle run
```

## 除錯技巧

### 1. 使用 IDE 除錯

```
1. 設置中斷點（Breakpoint）
2. 以除錯模式執行
3. 觀察變數值
4. 逐步執行
```

### 2. 命令列除錯

```bash
# 啟動除錯伺服器
java -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=5005 Main

# 使用 jdb 連接
jdb -attach 5005
```

## 常見問題

### 1. 找不到 class

可能原因：
1. 類別路徑（classpath）設置錯誤
2. 編譯輸出目錄不正確
3. 套件名稱不符

解決方法：
```bash
# 檢查類別路徑
echo $CLASSPATH

# 確認輸出目錄結構
tree bin/

# 使用 -cp 指定類別路徑
java -cp bin com.example.Main
```

### 2. 記憶體問題

```bash
# 增加堆積空間
java -Xmx1024m Main

# 顯示 GC 資訊
java -verbose:gc Main
```

### 3. 編碼問題

```bash
# 編譯時指定編碼
javac -encoding UTF-8 Main.java

# 執行時指定編碼
java -Dfile.encoding=UTF-8 Main
```

## 最佳實踐

### 1. 專案結構
- 使用標準的目錄結構
- 遵循套件命名慣例
- 保持良好的程式碼組織

### 2. 編譯與執行
- 使用建置工具（Maven/Gradle）
- 適當設置記憶體參數
- 注意類別路徑設置

### 3. 除錯與測試
- 善用 IDE 除錯工具
- 寫好單元測試
- 使用日誌記錄

## 進階主題

### 1. JAR 檔案

```bash
# 創建 JAR 檔案
jar cvf program.jar -C bin .

# 執行 JAR 檔案
java -jar program.jar
```

### 2. 多執行緒除錯

```bash
# 顯示執行緒資訊
jstack <pid>

# 執行時啟用執行緒監控
java -Xlog:threads Main
```

### 3. 效能調校

```bash
# 使用 JConsole 監控
jconsole

# 使用 VisualVM 分析
visualvm
```

## 學習資源

- [Java 官方文件](https://docs.oracle.com/en/java/)
- [OpenJDK 文件](https://openjdk.java.net/docs/)
- [Java 教學網站](https://www.oracle.com/java/technologies/learning-java.html)

## 版本控制整合

### Git 設定
```bash
# .gitignore 檔案
bin/
*.class
*.jar
.settings/
.classpath
.project
```

## 注意事項
1. 定期更新 JDK 版本
2. 注意安全性更新
3. 保持程式碼整潔
4. 做好版本控制

---

這份指南提供了 Java 開發的基礎到進階知識，建議根據需求逐步學習和實踐。
