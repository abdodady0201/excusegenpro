# 🎭 SmartExcuse AI - Flutter App

A production-ready Flutter app that generates AI-powered excuses with Material 3 UI, dark/light mode, favorites, and Pro subscription.

## 📁 Project Structure

```
lib/
├── main.dart                    # App entry point + ProviderScope
├── theme/
│   └── app_theme.dart           # Material 3 light/dark themes
├── models/
│   └── excuse.dart              # Excuse model, Situation & Tone enums
├── services/
│   ├── excuse_service.dart      # Excuse generation (20+ per category)
│   ├── storage_service.dart     # SharedPreferences: favorites, limits, pro
│   └── ad_service.dart          # AdMob unit IDs (test + production)
├── providers/
│   └── app_providers.dart       # Riverpod: theme, pro, excuses, favorites
├── widgets/
│   └── shared_widgets.dart      # GradientButton, SituationChip, ExcuseCard
└── screens/
    ├── splash_screen.dart        # Animated splash with brand identity
    ├── home_screen.dart          # Main generation screen
    ├── favorites_screen.dart     # Saved excuses with swipe-to-delete
    └── pro_screen.dart           # Subscription upsell screen
```

## 🚀 Setup & Run

### 1. Install dependencies
```bash
flutter pub get
```

### 2. Run the app
```bash
flutter run
```

## 🔑 AdMob Production Setup

### Android (`android/app/src/main/AndroidManifest.xml`)
Replace the test App ID:
```xml
<meta-data
    android:name="com.google.android.gms.ads.APPLICATION_ID"
    android:value="ca-app-pub-XXXXXXXXXXXXXXXX~XXXXXXXXXX"/>
```

### iOS (`ios/Runner/Info.plist`)
Add your real App ID:
```xml
<key>GADApplicationIdentifier</key>
<string>ca-app-pub-XXXXXXXXXXXXXXXX~XXXXXXXXXX</string>
```

### Update Ad Unit IDs in `lib/services/ad_service.dart`
Replace test IDs with your production Ad Unit IDs.

## 💳 In-App Purchases (Production)

This app uses a demo purchase flow. For production, integrate:
```yaml
# Add to pubspec.yaml
in_app_purchase: ^3.1.11
```

Then implement purchase verification in `lib/screens/pro_screen.dart`.

## ✨ Features

- **Material 3** with custom color scheme built from seed color
- **Dark/Light mode** toggle with persistent preference
- **Animated splash screen** with brand identity
- **4 situations** × **4 tones** = 80+ unique excuses
- **Daily limit** of 5 free generations (resets daily)
- **Favorites** with swipe-to-delete and share
- **Copy & Share** on any excuse
- **PRO screen** with pricing cards and feature list
- **Riverpod** state management throughout
- **AdMob** banner ad integration (disabled for Pro users)

## 📦 Dependencies

| Package | Purpose |
|---------|---------|
| `flutter_riverpod` | State management |
| `shared_preferences` | Local storage for favorites, limits, pro |
| `share_plus` | Native share sheet |
| `google_mobile_ads` | AdMob integration |
| `flutter_animate` | Animations and transitions |
