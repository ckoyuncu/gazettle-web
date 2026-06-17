# App Icon Assets

This directory contains the source icons for the Word Game app.

## Required Files

| File | Size | Purpose |
|------|------|---------|
| `app_icon.png` | 1024x1024 | Main app icon (iOS, Android legacy, Web) |
| `app_icon_foreground.png` | 1024x1024 | Foreground layer for Android adaptive icons |

## Current Placeholder Icons

The current icons are placeholders featuring:
- **Background**: Teal (#14B8A6) - matches app theme
- **Foreground**: White "W" letter - represents word game

## Replacing the Placeholder Icons

### Design Requirements

1. **app_icon.png**
   - Size: 1024x1024 pixels
   - Format: PNG with transparency (optional)
   - Content: Full icon including background
   - Safe zone: Keep important content within center 80% for rounded corners

2. **app_icon_foreground.png**
   - Size: 1024x1024 pixels
   - Format: PNG with transparency
   - Content: Foreground elements only (transparent background)
   - Safe zone: Keep content within center 66% (Android adaptive icons may be masked)

### Design Tips

- Keep the design simple and recognizable at small sizes (29x29 px)
- Use bold shapes and high contrast
- Avoid fine details that disappear at small sizes
- Test at multiple sizes: 29, 40, 60, 76, 83.5, 120, 152, 167, 180, 1024

## Regenerating App Icons

After replacing the source icons, regenerate platform-specific icons:

```bash
# Install dependencies if needed
flutter pub get

# Generate icons for all platforms
dart run flutter_launcher_icons
```

This will generate icons for:
- **iOS**: All required sizes in ios/Runner/Assets.xcassets/
- **Android**: Adaptive icons in android/app/src/main/res/
- **Web**: Favicon and icons in web/

## Icon Configuration

The icon configuration is in `pubspec.yaml`:

```yaml
flutter_launcher_icons:
  android: true
  ios: true
  image_path: "assets/icon/app_icon.png"
  adaptive_icon_background: "#14B8A6"
  adaptive_icon_foreground: "assets/icon/app_icon_foreground.png"
  ios_content_mode: center
  web:
    generate: true
    image_path: "assets/icon/app_icon.png"
```

## Platform-Specific Notes

### iOS
- Icons are automatically rounded by iOS
- Do not include rounded corners in source images
- Required sizes: 20, 29, 40, 60, 76, 83.5, 1024 (various @1x, @2x, @3x)

### Android
- Uses adaptive icons (separate foreground/background)
- Background color: #14B8A6 (teal)
- Foreground should work with circular, rounded square, and squircle masks
- Legacy icons also generated for older Android versions

### Web
- Generates favicon.png and icons-192.png, icons-512.png
- Used for PWA manifest and browser tabs

## Regeneration Script

A Dart script is available to regenerate placeholder icons:

```bash
dart run tool/generate_placeholder_icons.dart
```

This creates simple teal icons with a white "W" letter.
