Step-1: create and initialize in root (native_splash.yaml)
```yaml
flutter_native_splash:

  # Supports
  android: true
  ios: true
  web: false

  # Background
  color: "#d4e4ed"

  # Background Image, Logo and Branding
  background_image: "assets/startup/background.png"
  image: "assets/startup/logo.png"
  branding: "assets/startup/branding.png"

  background_image_dark: "assets/startup/background_dark.png"
  image_dark: "assets/startup/logo_dark.png"
  branding_dark: "assets/startup/branding_dark.png"

  android_12:
    color: "#d4e4ed"
    image: "assets/startup/android_logo.png"
    branding: "assets/startup/android_branding.png"
```

Step-2: build with terminal
dart run flutter_native_splash:create --path=native_splash.yaml

Step-3: Attach flutter_native_splash with flutter app:

```dart
void main() {
  final binding = WidgetsFlutterBinding.ensureInitialized();
  FlutterNativeSplash.preserve(widgetsBinding: binding);
  // ...
}
```

Step-4: Remove flutter_native_splash from flutter app (Call this from initState of root widget)
```dart
void _initialization() async {
  log("Native splash pushing...");
  await Future.delayed(const Duration(seconds: 15));
  FlutterNativeSplash.remove();
  log("Native splash removed");
}
```