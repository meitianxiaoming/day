# 每一天 📅

一个跨平台（Android & iOS）的节日计算器 App，帮助你记住每一个重要日子。

## ✨ 功能

- 🎂 **生日管理**：添加多人公历生日，自动换算农历
- 💝 **纪念日**：结婚纪念日、恋爱纪念日等
- 🎉 **节日提醒**：内置中国传统节日 + 自定义节日
- 🔔 **智能提醒**：前10天/5天/3天/当天，早上6:00推送
- ☁️ **云端备份**：Firebase 账号登录，数据同步不丢失
- 📱 **双平台**：一套代码，Android & iOS 通用

## 🚀 开始使用

### 环境要求

- Flutter SDK 3.2+
- Android Studio / Xcode
- Firebase 账号（用于认证和云端备份）

### 安装步骤

1. **安装 Flutter**
   ```bash
   # 从官网下载并安装 Flutter SDK
   https://flutter.dev/docs/get-started/install
   ```

2. **克隆项目**
   ```bash
   cd everyday
   flutter pub get
   ```

3. **配置 Firebase**
   - 在 [Firebase Console](https://console.firebase.google.com/) 创建项目
   - 下载 `google-services.json` 放到 `android/app/` 目录
   - 下载 `GoogleService-Info.plist` 放到 `ios/Runner/` 目录

4. **运行**
   ```bash
   flutter run
   ```

## 📁 项目结构

```
lib/
├── main.dart                 # 入口文件
├── app.dart                  # App 主组件 + 导航
├── models/
│   └── event.dart            # 事件数据模型
├── database/
│   └── database_helper.dart  # SQLite 数据库操作
├── utils/
│   └── lunar_calendar.dart   # 农历转换算法
├── services/
│   ├── notification_service.dart  # 推送通知
│   └── auth_service.dart     # 认证 & 云端备份
├── screens/
│   ├── home_screen.dart      # 首页
│   ├── add_screen.dart       # 添加选择页
│   ├── add_person_screen.dart # 添加生日
│   ├── add_event_screen.dart  # 添加纪念日/节日
│   ├── event_detail_screen.dart # 事件详情
│   └── settings_screen.dart  # 设置 & 登录
├── widgets/
│   └── event_card.dart       # 事件卡片组件
└── theme/
    └── app_theme.dart        # 淡黄色主题
```

## 🎨 UI 预览

- 主色调：淡黄色 (#FFE082)
- 风格：简洁、直观
- Material 3 设计语言

## 🔧 技术栈

| 技术 | 用途 |
|------|------|
| Flutter | 跨平台框架 |
| sqflite | 本地数据库 |
| Firebase Auth | 邮箱/手机号登录 |
| Cloud Firestore | 云端数据存储 |
| flutter_local_notifications | 本地推送通知 |
| WorkManager | 后台任务调度 |

## 📄 License

MIT
