# Expo CLI 完整使用指南

## 目錄
- [基礎知識](#基礎知識)
- [環境準備](#環境準備)
- [專案建立](#專案建立)
- [開發伺服器](#開發伺服器)
- [常用指令](#常用指令)
- [建置與部署](#建置與部署)
- [疑難排解](#疑難排解)

## 基礎知識

Expo 是 React Native 的工具鏈與平台，適合快速建立、測試、發佈跨平台 App。

## 環境準備

```bash
node --version
npm --version
```

## 專案建立

```bash
npx create-expo-app MyApp
cd MyApp
npx expo start
```

## 開發伺服器

```bash
npx expo start
npx expo start -c
npx expo start --tunnel
```

## 常用指令

```bash
npx expo install expo-camera
npx expo doctor
npx expo config
```

## 建置與部署

```bash
npm install -g eas-cli
eas login
eas build --platform all
eas submit --platform android
```

## 疑難排解

1. 快取問題：`npx expo start -c`
2. 依賴衝突：刪除 `node_modules` 後重新安裝
3. 裝置連線問題：改用 `--tunnel`
