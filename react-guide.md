# Expo CLI 完整使用指南

## 目錄
- [基礎知識](#基礎知識)
- [環境準備](#環境準備)
- [專案建立](#專案建立)
- [開發伺服器](#開發伺服器)
- [專案結構](#專案結構)
- [常用指令](#常用指令)
- [除錯與測試](#除錯與測試)
- [建置與部署](#建置與部署)
- [疑難排解](#疑難排解)
- [最佳實踐](#最佳實踐)

## 基礎知識

### 什麼是 Expo？
Expo 是一個用於構建 React Native 應用程式的框架和平台，主要特點：
1. 快速開發 iOS 和 Android 應用
2. 無需 Xcode 或 Android Studio 即可開始開發
3. 提供豐富的原生 API 和組件
4. 支援即時更新和熱重載

### Expo 的優點
- **快速上手**：無需配置複雜的原生開發環境
- **跨平台**：一次編寫，多平台運行
- **開發工具**：內建開發者工具和除錯功能
- **OTA 更新**：支援無需重新提交商店的即時更新

### Expo 版本選擇
1. **Expo Go**（開發測試）
   - 適合快速原型開發
   - 手機安裝 Expo Go App 即可測試

2. **Development Build**（自訂原生代碼）
   - 需要額外的原生模組
   - 更接近正式產品環境

## 環境準備

### 系統需求
- **Node.js**：建議 18.x 或更新版本
- **npm** 或 **yarn**：套件管理工具
- **Git**：版本控制（選用）

### 安裝 Node.js
```bash
# 檢查 Node.js 版本
node --version

# 檢查 npm 版本
npm --version
```

### 安裝 Expo Go App
1. **iOS**：從 App Store 下載 Expo Go
2. **Android**：從 Google Play 下載 Expo Go

## 專案建立

### 建立新專案
```bash
# 基本語法
npx create-expo-app MyFirstApp

# 使用特定範本
npx create-expo-app MyApp --template blank

# 使用 TypeScript 範本
npx create-expo-app MyApp --template blank-typescript
```

### 範本類型
- **blank**：最小化專案，適合從零開始
- **blank-typescript**：TypeScript 版本
- **tabs**：包含底部導航欄的範本
- **bare-minimum**：接近原生的最小配置

### 進入專案目錄
```bash
cd MyFirstApp
```

## 開發伺服器

### 啟動開發伺服器
```bash
# 標準啟動
npx expo start

# 清除快取啟動
npx expo start -c

# 使用特定模式啟動
npx expo start --tunnel  # 穿透防火牆
npx expo start --lan     # 區域網路模式
npx expo start --localhost  # 本機模式
```

### 開發伺服器選項
```bash
# 直接在 Android 模擬器開啟
npx expo start --android

# 直接在 iOS 模擬器開啟
npx expo start --ios

# 在瀏覽器開啟
npx expo start --web

# 離線模式
npx expo start --offline
```

### 互動式快捷鍵
啟動開發伺服器後，可使用以下快捷鍵：
- `a` - 在 Android 模擬器/裝置開啟
- `i` - 在 iOS 模擬器開啟
- `w` - 在網頁瀏覽器開啟
- `r` - 重新載入應用程式
- `m` - 切換選單
- `j` - 開啟除錯工具

## 專案結構

### 標準專案結構
```
MyFirstApp/
├── .expo/              # Expo 快取和配置
├── assets/             # 靜態資源
│   ├── icon.png       # 應用圖示
│   ├── splash.png     # 啟動畫面
│   └── adaptive-icon.png  # Android 自適應圖示
├── node_modules/       # 依賴套件
├── .gitignore         # Git 忽略檔案
├── app.json           # Expo 配置檔
├── App.js             # 主要應用入口
├── babel.config.js    # Babel 配置
└── package.json       # 專案依賴定義
```

### app.json 配置說明
```json
{
  "expo": {
    "name": "MyFirstApp",
    "slug": "my-first-app",
    "version": "1.0.0",
    "orientation": "portrait",
    "icon": "./assets/icon.png",
    "splash": {
      "image": "./assets/splash.png",
      "resizeMode": "contain",
      "backgroundColor": "#ffffff"
    },
    "ios": {
      "bundleIdentifier": "com.yourcompany.myfirstapp"
    },
    "android": {
      "package": "com.yourcompany.myfirstapp"
    }
  }
}
```

## 常用指令

### 套件管理
```bash
# 安裝 Expo SDK 套件
npx expo install expo-camera

# 安裝多個套件
npx expo install expo-location expo-sensors

# 安裝 npm 套件
npm install axios

# 更新所有依賴
npx expo install --fix
```

### 專案資訊
```bash
# 查看專案配置
npx expo config

# 檢查專案狀態
npx expo doctor

# 查看 Expo CLI 版本
npx expo --version
```

### 登入與帳號管理
```bash
# 登入 Expo 帳號
npx expo login

# 登出
npx expo logout

# 查看當前使用者
npx expo whoami
```

## 除錯與測試

### 開啟除錯工具
```bash
# 啟動時開啟開發者選單
# 在實體裝置上搖動手機
# 在模擬器上使用 Cmd+D (iOS) 或 Cmd+M (Android)
```

### React DevTools
```bash
# 安裝 React DevTools
npm install -g react-devtools

# 啟動 DevTools
react-devtools
```

### 錯誤追蹤
```javascript
// 在程式碼中使用 console
console.log('除錯訊息');
console.warn('警告訊息');
console.error('錯誤訊息');
```

### 效能監控
```javascript
import { LogBox } from 'react-native';

// 忽略特定警告
LogBox.ignoreLogs(['Warning: ...']);

// 忽略所有警告（不建議）
LogBox.ignoreAllLogs();
```

## 建置與部署

### 建置獨立應用
```bash
# 建置 Android APK
eas build --platform android

# 建置 iOS IPA
eas build --platform ios

# 同時建置兩個平台
eas build --platform all
```

### EAS (Expo Application Services)
```bash
# 安裝 EAS CLI
npm install -g eas-cli

# 登入 EAS
eas login

# 配置專案
eas build:configure

# 提交到商店
eas submit --platform ios
eas submit --platform android
```

### 發佈更新
```bash
# 發佈更新到 Expo
npx expo publish

# 使用 EAS Update
eas update --branch production --message "Bug fixes"
```

## 疑難排解

### 清除快取問題
```bash
# 清除 Expo 快取
npx expo start -c

# 清除 npm 快取
npm cache clean --force

# 刪除 node_modules 重新安裝
rm -rf node_modules
npm install

# 清除 watchman 快取（macOS/Linux）
watchman watch-del-all
```

### Metro Bundler 問題
```bash
# 重置 Metro Bundler
npx expo start --clear

# 指定不同 port
npx expo start --port 8081
```

### 常見錯誤解決

1. **找不到模組錯誤**
   ```bash
   # 重新安裝依賴
   rm -rf node_modules package-lock.json
   npm install
   ```

2. **iOS 模擬器無法啟動**
   ```bash
   # 檢查 Xcode Command Line Tools
   xcode-select --install
   ```

3. **Android 模擬器連接問題**
   ```bash
   # 檢查 ADB 連接
   adb devices
   
   # 重啟 ADB
   adb kill-server
   adb start-server
   ```

4. **網路連接問題**
   ```bash
   # 使用 tunnel 模式
   npx expo start --tunnel
   ```

### 除錯檢查清單
- [ ] 確認 Node.js 版本是否符合需求
- [ ] 檢查網路連接是否正常
- [ ] 確認手機和電腦在同一網路
- [ ] 清除所有快取後重試
- [ ] 檢查防火牆設定
- [ ] 查看 Expo 開發者論壇

## 最佳實踐

### 專案組織
1. **模組化結構**
   ```
   src/
   ├── components/    # 可重用元件
   ├── screens/       # 畫面元件
   ├── navigation/    # 導航配置
   ├── utils/         # 工具函數
   ├── hooks/         # 自訂 Hooks
   └── constants/     # 常數定義
   ```

2. **命名規範**
   - 元件使用 PascalCase：`UserProfile.js`
   - 工具函數使用 camelCase：`formatDate.js`
   - 常數使用 UPPER_SNAKE_CASE：`API_KEY`

### 效能優化
```javascript
// 使用 React.memo 避免不必要的重新渲染
import React, { memo } from 'react';

const MyComponent = memo(({ data }) => {
  return <View>{data}</View>;
});

// 使用 useCallback 快取函數
import { useCallback } from 'react';

const handlePress = useCallback(() => {
  console.log('按鈕被點擊');
}, []);
```

### 程式碼品質
```bash
# 安裝 ESLint
npm install --save-dev eslint

# 安裝 Prettier
npm install --save-dev prettier

# 設定 pre-commit hook
npm install --save-dev husky lint-staged
```

### 環境變數管理
```bash
# 安裝 dotenv
npm install dotenv

# 建立 .env 檔案
API_URL=https://api.example.com
API_KEY=your_api_key_here
```

### 版本控制
```bash
# .gitignore 重要項目
node_modules/
.expo/
.expo-shared/
*.log
.env
.DS_Store
```

### 測試策略
```bash
# 安裝 Jest 和測試工具
npm install --save-dev jest @testing-library/react-native

# 執行測試
npm test
```

## 實用資源
- [Expo 官方文件](https://docs.expo.dev/)
- [React Native 官方文件](https://reactnative.dev/)
- [Expo GitHub](https://github.com/expo/expo)
- [Expo 論壇](https://forums.expo.dev/)
- [Expo Discord 社群](https://chat.expo.dev/)

## 進階主題

### 自訂原生模組
```bash
# 建立 development build
npx expo prebuild

# 執行 iOS
npx expo run:ios

# 執行 Android
npx expo run:android
```

### 使用 Expo Router
```bash
# 安裝 Expo Router
npx expo install expo-router react-native-safe-area-context react-native-screens

# 建立檔案路由結構
app/
├── _layout.js
├── index.js
└── [id].js
```

### 整合第三方服務
```bash
# Firebase
npx expo install firebase

# OneSignal 推播通知
npx expo install onesignal-expo-plugin

# Sentry 錯誤追蹤
npx expo install @sentry/react-native
```

## 注意事項
1. 定期更新 Expo SDK 至穩定版本
2. 遵循 React Native 和 Expo 的最佳實踐
3. 注意不同平台的 API 差異
4. 保持專案依賴的一致性
5. 做好環境變數和敏感資訊的保護
6. 定期備份專案和配置檔案

## 快速參考卡

### 最常用指令
```bash
npx create-expo-app MyApp    # 建立專案
npx expo start                # 啟動開發伺服器
npx expo start -c             # 清除快取啟動
npx expo install package      # 安裝套件
npx expo doctor               # 檢查專案健康度
eas build                     # 建置應用
```

### 常用快捷鍵
- `a` - Android
- `i` - iOS
- `w` - Web
- `r` - Reload
- `c` - Clear cache

---

這份指南涵蓋了 Expo CLI 的完整使用方法，從基礎到進階應用。建議循序漸進學習，遇到問題時參考疑難排解章節。祝開發順利！