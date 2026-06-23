# Habi(하찮은 비서)

하찮지만 귀여운 AI 모바일 비서 앱입니다. 'Habi'(하찮은 비서) 는 사용자의 일정, 할 일, 준비물과 생활 정보를 기억하고 아침 브리핑과 알림을 통해 먼저 챙겨줍니다.

## 현재 개발 범위

- 소셜 로그인과 온보딩
- 개인화 프로필 관리
- AI 채팅을 통한 일정·할 일 등록
- 날씨, 일정, 준비물 아침 브리핑
- 일정·할 일·챙길 것 로컬 관리
- 브리핑 시간 로컬 알림

## 기술 스택

- Flutter / Dart
- Riverpod
- GoRouter
- Drift (SQLite) / SharedPreferences
- Dio
- Firebase Authentication / Cloud Functions
- Flutter Local Notifications
- Freezed / JSON Serializable

## 지원 플랫폼

- iOS 15.0 이상 우선 개발
- Android 9.0(API 28) 이상

Android 앱은 Android 16(API 36)을 기준으로 컴파일·타겟하며, NDK 28.2를 사용합니다.

## 개발 환경

- Flutter 3.44.3 (stable)
- Dart 3.12.2
- iOS: Xcode, Swift Package Manager
- Android: Android Studio, Android SDK

환경 상태는 다음 명령으로 확인합니다.

```bash
flutter doctor -v
```

## 프로젝트 준비

저장소를 받은 후 의존성을 설치합니다.

```bash
flutter pub get
```

Firebase 기능을 개발하려면 개발용 Firebase 프로젝트를 생성한 후 FlutterFire를 설정해야 합니다.

```bash
dart pub global activate flutterfire_cli
flutterfire configure
```

Firebase 클라이언트 설정은 개발·운영 환경별로 분리합니다. Anthropic 등 서버 API 키는 앱에 포함하지 않고 Cloud Functions의 Secret으로 관리합니다.

## 실행

사용 가능한 디바이스를 확인합니다.

```bash
flutter devices
```

연결된 기본 디바이스에서 실행합니다.

```bash
flutter run
```

특정 디바이스를 지정하려면:

```bash
flutter run -d <device-id>
```

iOS Simulator는 Xcode에서 시뮬레이터를 먼저 실행한 후 `flutter run`을 사용합니다. 실기기 실행에는 Xcode Signing 설정이 필요합니다.

## 개발 명령

| 목적             | 명령                                                       |
| ---------------- | ---------------------------------------------------------- |
| 패키지 설치      | `flutter pub get`                                          |
| 정적 분석        | `flutter analyze`                                          |
| 전체 테스트      | `flutter test`                                             |
| 코드 포맷        | `dart format .`                                            |
| 코드 생성        | `dart run build_runner build --delete-conflicting-outputs` |
| 코드 생성 감시   | `dart run build_runner watch --delete-conflicting-outputs` |
| 의존성 상태 확인 | `flutter pub outdated`                                     |

Freezed, JSON Serializable, Drift 모델이 변경되면 코드 생성 명령을 실행해야 합니다. 생성된 `*.freezed.dart`, `*.g.dart`는 소스와 함께 커밋합니다.

## 릴리스 빌드

```bash
# iOS
flutter build ipa --release

# Android
flutter build appbundle --release
```

릴리스 빌드 전에 `flutter analyze`와 `flutter test`를 모두 통과해야 합니다.
