# Flutter 完整使用指南

## 目錄
- [基礎知識](#基礎知識)
- [環境準備](#環境準備)
- [專案建立](#專案建立)
- [專案結構](#專案結構)
- [常用指令](#常用指令)
- [測試與建置](#測試與建置)
- [最佳實踐](#最佳實踐)

## 基礎知識

### 什麼是 Flutter？
Flutter 是 Google 推出的跨平台 UI 框架，使用 Dart 開發，可同時部署到 iOS、Android、Web 與 Desktop。

主要優點：
1. 單一程式碼庫多平台
2. UI 一致性高
3. Hot Reload 提升開發效率
4. 生態完整（套件、工具、社群）

## 環境準備

- 安裝 Flutter SDK
- 安裝 Android Studio / Xcode（依平台）
- 設定模擬器或實機

```bash
flutter --version
flutter doctor
```

## 專案建立

```bash
flutter create my_flutter_app
cd my_flutter_app
flutter run
```

## 專案結構

- `lib/main.dart`：應用入口
- `lib/`：主要業務邏輯與畫面
- `test/`：測試程式
- `pubspec.yaml`：依賴與資源設定

## 常用指令

```bash
# 下載依賴
flutter pub get

# 執行程式
flutter run

# 列出裝置
flutter devices

# 清除建置快取
flutter clean
```

## 測試與建置

```bash
# 單元/元件測試
flutter test

# Android 發佈包
flutter build apk

# iOS 發佈包
flutter build ios
```

## 最佳實踐

1. 採用 feature-based 目錄結構
2. 使用狀態管理（Provider / Riverpod / Bloc）保持可維護性
3. 對核心流程撰寫 widget test
4. 使用環境分離（dev/stage/prod）
5. 定期執行 `flutter doctor` 與依賴更新
