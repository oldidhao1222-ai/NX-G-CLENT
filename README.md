# NX G CLIENT

A native Android companion app for Minecraft Bedrock Edition, using a minimal black-and-white design.

## Current implementation

- Branded home screen and navigation-ready layout.
- Detects whether the standard Minecraft Bedrock Android package is visible to the app.
- Launches Minecraft when Android reports a launch intent.
- Lets users select `.mcpack`, `.mcaddon`, and ZIP files through Android's document picker.
- Performs a basic archive/`manifest.json` check and displays results.
- Offers Android's share chooser to pass a selected pack to a compatible app.
- Persists the Reduce Motion preference.
- Includes an app icon, basic unit test, and Gradle project configuration.

## Important limitations

This is a companion application, not a replacement for the Minecraft Bedrock game client. Android and Minecraft versions determine whether a selected pack can be handed off to Minecraft. The app does not inject code into Minecraft, alter protected game binaries, or guarantee that Minecraft accepts a pack from the share chooser. A successful manifest scan is not a guarantee that a pack works in-game. `mcaddon` files can contain nested packs and may require opening/importing through Minecraft or a file manager.

The app intentionally does not claim to read Minecraft's exact in-game version; Android does not provide a reliable public API for that.

## Requirements

- Android Studio with Android SDK Platform 35 installed
- JDK 17
- Android Gradle Plugin 8.7.3
- Kotlin 2.0.21
- Android device/emulator running Android 8.0 (API 26) or newer

Gradle may need internet access to download dependencies on first sync.

## Open and build

1. Extract this project ZIP.
2. Open the `NX_G_CLIENT` folder in Android Studio.
3. Allow Gradle sync to complete.
4. Confirm JDK 17 is selected in Android Studio.
5. Run the `app` configuration on a device or emulator.

From a terminal in the project root:

```bash
./gradlew assembleDebug
./gradlew test
```

On Windows:

```bat
gradlew.bat assembleDebug
gradlew.bat test
```

The debug APK is normally generated at:

`app/build/outputs/apk/debug/app-debug.apk`

This source bundle does not include a Gradle wrapper JAR, SDK, signing key, or precompiled APK. If Android Studio prompts to generate/update the Gradle wrapper, use a compatible Gradle 8.9 distribution for AGP 8.7.x. The APK path above exists only after a successful build.

## Release build

Configure signing credentials locally and securely before creating a release APK. Do not commit keystores, passwords, or private keys to source control. Build with `assembleRelease` after configuring signing.

## Package identity

- App name: NX G CLIENT
- Application ID: `com.nxg.client`
- Version: `1.0.0`

## Disclaimer

Minecraft is a trademark of Mojang Synergies AB. NX G CLIENT is an independent companion app and is not affiliated with or endorsed by Mojang or Microsoft.


## Optional cloud build with GitHub Actions

The repository includes `.github/workflows/android.yml`. Upload the project to a GitHub repository, then open **Actions → Build NX G CLIENT APK → Run workflow**. The workflow installs JDK 17 and Android SDK Platform 35, runs `assembleDebug` and `test`, and publishes the debug APK as a downloadable workflow artifact if the build succeeds.

The workflow has been added but has not been run from this environment. It is not proof that the project compiles; check the GitHub Actions result and logs.
