# 高校社团管理系统

> [English Version](README.en.md)

一个多平台的高校社团管理系统，包含 **Web 管理端**、**Java 后端** 和 **Android 客户端**，覆盖社团全生命周期管理。

## 项目结构

```
club-manage/
├── club-manage-web/        # Web 前端 — React + TypeScript + Vite
├── club-manage-backend/    # 后端服务 — Spring Boot 3 + MyBatis-Plus + MySQL
└── club-manage-android/    # Android 客户端 — Kotlin + Jetpack Compose
```

## 功能概览

### 用户系统
- 注册 / 登录（密码或验证码）
- 个人资料编辑、密码修改、账户注销
- 图形验证码、手机 / 邮箱验证码

### 社团管理
- 创建社团（需管理员审核）
- 浏览社团列表（支持模糊搜索）
- 申请加入 / 退出社团（需社团管理员审核）
- 社团成员管理
- 社团管理员指派
- 解散社团

### 活动管理
- 发布活动（需管理员审核）
- 浏览活动列表（支持搜索）
- 报名 / 取消报名活动
- 活动参与者审核
- 活动总结与结束

### 评分系统
- 对社团进行评分
- 修改或撤回评分
- 查看社团平均分

### 管理后台
- 用户管理（分页、搜索、编辑）
- 社团创建审核
- 活动发布审核
- 社团信息查询

## 技术栈

### Web 前端 (`club-manage-web`)

| 技术 | 说明 |
|------|------|
| React 19 | UI 框架 |
| TypeScript | 语言 |
| Vite | 构建工具 |
| React Router | 前端路由 |
| Tailwind CSS | 样式 |

### 后端 (`club-manage-backend`)

| 技术 | 说明 |
|------|------|
| Spring Boot 3.3 | 应用框架 |
| Java 17 | 语言 |
| MyBatis-Plus 3.5 | ORM |
| MySQL 8 | 数据库 |
| Redis | 缓存（验证码存储） |
| JWT | 认证 |
| QQ 邮箱 / 阿里云短信 | 验证码发送 |

### Android (`club-manage-android`)

| 技术 | 说明 |
|------|------|
| Kotlin 2.0 | 语言 |
| Jetpack Compose + Material 3 | UI |
| Navigation Compose | 路由 |
| Retrofit | HTTP 客户端 |
| Coil | 图片加载 |
| 最低 SDK 26 / 目标 SDK 34 | |

## 快速开始

### 1. 启动后端

```bash
cd club-manage-backend

# 配置数据库和 Redis（编辑 application.properties）
# - MySQL 中创建名为 club 的数据库
# - 配置 Redis 连接
# - 配置邮箱/短信

# 启动
./mvnw spring-boot:run
```

后端默认运行在 `http://localhost:8080`。

### 2. 启动 Web 前端

```bash
cd club-manage-web
npm install
npm run dev
```

Web 端默认运行在 `http://localhost:5173`（Vite 默认端口）。

### 3. 构建 Android 应用

用 Android Studio 打开 `club-manage-android` 目录，或使用命令行：

```bash
cd club-manage-android
./gradlew assembleDebug
```

APK 输出路径：`app/build/outputs/apk/debug/app-debug.apk`

## API 概览

所有受保护的接口通过 `Authorization: Bearer <token>` 进行认证。

| 路径 | 说明 |
|------|------|
| `/api/user/**` | 用户认证与资料 |
| `/api/club/**` | 社团 CRUD |
| `/api/member/**` | 社团成员管理 |
| `/api/activities/**` | 活动管理 |
| `/api/registration/**` | 活动报名 |
| `/api/rating/**` | 评分 |
| `/api/admin/**` | 管理操作 |
