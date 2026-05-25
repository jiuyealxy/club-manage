# Club Management System

> [中文版](README.md)

A multi-platform university club management system with a **Web frontend**, **Java backend**, and **Android client**, covering the full lifecycle of club management.

## Project Structure

```
club-manage/
├── club-manage-web/        # Web Frontend — React + TypeScript + Vite
├── club-manage-backend/    # Backend API — Spring Boot 3 + MyBatis-Plus + MySQL
└── club-manage-android/    # Android App — Kotlin + Jetpack Compose
```

## Features

### User System
- Sign up / Sign in (password or verification code)
- Profile editing, password reset, account deletion
- CAPTCHA, email / SMS verification

### Club Management
- Create a club (pending admin approval)
- Browse clubs (fuzzy search supported)
- Join / leave a club (pending club admin approval)
- Member list management
- Assign / revoke club admin roles
- Dissolve a club

### Activity Management
- Publish an activity (pending admin approval)
- Browse activities (search supported)
- Register for / cancel an activity
- Review activity registrations
- Conclude an activity with a summary

### Rating System
- Rate a club
- Update or withdraw your rating
- View average ratings for all clubs

### Admin Dashboard
- User management (pagination, search, edit)
- Club creation review
- Activity publication review
- Club information lookup

## Tech Stack

### Web Frontend (`club-manage-web`)

| Technology | Description |
|------------|-------------|
| React 19 | UI framework |
| TypeScript | Language |
| Vite | Build tool |
| React Router | Client-side routing |
| Tailwind CSS | Styling |

### Backend (`club-manage-backend`)

| Technology | Description |
|------------|-------------|
| Spring Boot 3.3 | Application framework |
| Java 17 | Language |
| MyBatis-Plus 3.5 | ORM |
| MySQL 8 | Database |
| Redis | Caching (verification codes) |
| JWT | Authentication |
| QQ Mail / Aliyun SMS | Verification code delivery |

### Android (`club-manage-android`)

| Technology | Description |
|------------|-------------|
| Kotlin 2.0 | Language |
| Jetpack Compose + Material 3 | UI framework |
| Navigation Compose | Routing |
| Retrofit | HTTP client |
| Coil | Image loading |
| Min SDK 26 / Target SDK 34 | |

## Quick Start

### 1. Start the Backend

```bash
cd club-manage-backend

# Configure database and Redis (edit application.properties)
# - Create a MySQL database named "club"
# - Configure Redis connection
# - Configure email/SMS settings

# Launch
./mvnw spring-boot:run
```

The backend runs at `http://localhost:8080` by default.

### 2. Start the Web Frontend

```bash
cd club-manage-web
npm install
npm run dev
```

The web frontend runs at `http://localhost:5173` by default.

### 3. Build the Android App

Open `club-manage-android` in Android Studio, or build via command line:

```bash
cd club-manage-android
./gradlew assembleDebug
```

APK output: `app/build/outputs/apk/debug/app-debug.apk`

## API Overview

All protected endpoints use `Authorization: Bearer <token>` header.

| Path | Description |
|------|-------------|
| `/api/user/**` | Authentication & profile |
| `/api/club/**` | Club CRUD |
| `/api/member/**` | Club membership management |
| `/api/activities/**` | Activity management |
| `/api/registration/**` | Activity registration |
| `/api/rating/**` | Club ratings |
| `/api/admin/**` | Admin operations |
