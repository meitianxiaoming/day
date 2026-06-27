# 「每一天」打包 & 分享指南

---

## 🚀 方法一：自己打包 APK（免费，最快）

### 第一步：安装 Flutter

1. 打开浏览器，访问 https://flutter.dev/docs/get-started/install/windows
2. 下载 Flutter SDK zip 包
3. 解压到 `C:\flutter`（不要放在 Program Files 等需要管理员权限的目录）
4. 把 `C:\flutter\bin` 添加到系统环境变量 PATH：
   - 右键「此电脑」→ 属性 → 高级系统设置 → 环境变量
   - 在 Path 里新增一条 `C:\flutter\bin`
5. 打开命令行（cmd），输入 `flutter doctor` 检查
6. 按提示安装缺失的组件（Android SDK 等）

### 第二步：安装依赖

```bash
cd 你的项目目录\everyday
flutter pub get
```

### 第三步：配置 Firebase（可选，不配也能用本地功能）

如果暂时不需要云端备份，可以先跳过。需要的话：
1. 访问 https://console.firebase.google.com/
2. 创建项目 → 添加 Android 应用（包名：com.everyday.app）
3. 下载 `google-services.json` 放到 `android/app/` 目录

### 第四步：打包

```bash
# 打 APK（发给 Android 用户）
flutter build apk --release

# 或者打 AppBundle（上架 Google Play 用）
flutter build appbundle --release
```

### 第五步：分享

打包完成后，文件在：
```
build\app\outputs\flutter-apk\app-release.apk
```

把这个 `.apk` 文件通过微信/QQ/网盘发给别人即可。

**对方安装时**：需要在手机「设置 → 安全 → 允许安装未知来源应用」里开启。

---

## 📲 方法二：用 GitHub Actions 自动打包（推荐长期使用）

不需要自己装任何东西，代码推送到 GitHub 自动构建：

1. 在 GitHub 新建仓库，把项目代码推送上去
2. 在项目根目录创建 `.github/workflows/build.yml`：

```yaml
name: Build APK
on:
  push:
    branches: [main]
  workflow_dispatch:  # 手动触发

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: subosito/flutter-action@v2
        with:
          flutter-version: '3.19.0'
      - run: flutter pub get
      - run: flutter build apk --release
      - uses: actions/upload-artifact@v4
        with:
          name: app-release
          path: build/app/outputs/flutter-apk/app-release.apk
```

3. 每次推送代码，GitHub 自动帮你打包，去 Actions 页面下载 APK 即可。

---

## 🍎 方法三：iOS 打包（给苹果用户）

需要 Mac 电脑 + Apple Developer 账号（$99/年）：

```bash
flutter build ios --release
```

然后用 Xcode 上传到 App Store 或通过 TestFlight 分发。

---

## ⚡ 快速开始（如果你不想自己装 Flutter）

我可以帮你把项目推送到 GitHub，配置好自动构建。之后你只需要：
1. 在 GitHub 网页上点一个按钮
2. 等几分钟
3. 下载 APK 发给别人

要我帮你这样做吗？
