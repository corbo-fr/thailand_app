# Thailand App

A one-screen Flutter layout from February 2021 by [Mathis Bois](https://github.com/corbo-fr) ([@corbo-fr](https://github.com/corbo-fr)). The page is a static French travel screen, **Voyage Thaïlande**, written to practice Flutter widgets. It is a single route with no booking flow and no API client.

![Voyage Thaïlande on iOS](.demo/ios_screen.png)
![Voyage Thaïlande on Android](.demo/android_screen.png)

The screenshots in `.demo/` were captured in February 2021.

## Screen

The whole interface is [`lib/main.dart`](lib/main.dart): one `StatelessWidget`, with each block stored as a top-level `Widget` and stacked in a scrolling `Column`.

The launcher name is `thailand_app`. The cyan app bar title is **Voyage Thaïlande**. `MaterialApp.title` is `Design Flutter` (the title the OS uses, not a second heading on the page). The debug banner is off.

From top to bottom:

1. A full-width header loaded with `Image.network` from `https://pullman.accor.com/destinations/country/thailand-1400x788-1.jpg`.
2. **Bienvenue au paradis**, then **Réservez votre séjour en Thaïlande**.
3. A French paragraph on Thailand: the former name Siam, the borders, Bangkok, Thai, and the baht.
4. Three cyan Material icons with labels: **HOTELS** (hotel), **VOLS** (flight), **VOITURES** (car).
5. A second French paragraph on the constitutional monarchy since 1932.
6. Two rounded photos, [`images/hotel_1.jpeg`](images/hotel_1.jpeg) and [`images/hotel_2.jpeg`](images/hotel_2.jpeg), each drawn at 180×120 with a corner radius of 20.
7. A cyan **Voir plus de logements** button.

The header needs a network connection. The hotel photos are bundled in the app. If that remote file is no longer available, the header does not appear and the rest of the page still builds.

[`images/cat.jpeg`](images/cat.jpeg) and [`images/catgif.gif`](images/catgif.gif) are in the repository. They are not listed under `flutter: assets` and the page does not display them.

## Interaction

The controls are drawn and left inert:

- The menu `IconButton` sets `onPressed` to `null`.
- The bookmark `IconButton` omits `onPressed`.
- **HOTELS**, **VOLS**, and **VOITURES** are `Icon` and `Text` widgets, with no gesture detector.
- **Voir plus de logements** is a `RaisedButton` whose callback is empty.

A tap stays on this screen.

## Stack

| | |
| --- | --- |
| UI | Flutter Material, one screen |
| Language | Dart, SDK constraint `>=2.7.0 <3.0.0` (before null safety) |
| Flutter | 1.22.6 stable, revision `9b2d32b605630f28625709ebd9d78ab3016b2bf6` (`.metadata`) |
| Dart in that release | 2.10.5 |
| Version | 1.0.0+1 (`pubspec.yaml`) |
| Android | application id `com.example.thailand_app`, minSdk 16, targetSdk and compileSdk 29, Gradle 5.6.2, Android Gradle Plugin 3.5.0, Kotlin 1.3.50 |
| iOS | bundle id `com.example.thailand_app`, deployment target 9.0 |
| Targets in the repo | Android and iOS |

`pubspec.yaml` also lists `cupertino_icons` 1.0.0, `english_words` 3.1.5, `google_fonts` 1.1.2, and `animate_do` 1.7.5. `lib/main.dart` imports only `package:flutter/material.dart`, so those packages are unused. There is no `test/` directory.

The original README recorded the machine setup used for this project: Flutter 1.22.6, Java 8 update 281, Android Studio 4.2 preview, Xcode 12.4, and the Flutter and Dart extensions in Visual Studio Code.

`RaisedButton`, the Dart 2 SDK bound, Gradle 5.6.2, and Android Gradle Plugin 3.5.0 belong to that 2021 toolchain. Building the project means using Flutter 1.22.6. Current Flutter stable releases have moved past these APIs and Gradle versions.

## Run

Install Flutter 1.22.6 (Dart 2.10.5) and JDK 8, then:

```bash
flutter --version
flutter pub get
flutter devices
flutter run
```

`flutter run` launches the app on the selected Android emulator or iOS simulator. Pass `-d <deviceId>` when more than one device is connected. Android Studio 4.2 (the preview recorded at the time) supplies the Android emulator. Xcode 12.4 supplies the iOS simulator, on macOS.

Release builds in `android/app/build.gradle` are signed with the debug keystore.

## Repository

```
lib/main.dart                                          # the whole UI
images/hotel_1.jpeg                                    # bundled hotel photo
images/hotel_2.jpeg                                    # bundled hotel photo
.demo/ios_screen.png                                   # screenshot above
.demo/android_screen.png                               # screenshot above
android/                                                # Android project
ios/                                                    # iOS project
pubspec.yaml
```

The Android entry point is `android/app/src/main/kotlin/com/example/choupi/MainActivity.kt`. Its `package` declaration and the application id are both `com.example.thailand_app`.

## Author

[Mathis Bois](https://github.com/corbo-fr) · [@corbo-fr](https://github.com/corbo-fr)

First commit: 17 February 2021.
