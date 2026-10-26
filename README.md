# CraftFarm Android — Source Project

CraftFarm is an offline-first Android app for tracking automated Minecraft Java farms. It uses a local HTML/JavaScript interface inside an Android WebView. Farm completion, build queue, notes, and material checkboxes are saved to WebView localStorage on this device.

## Important delivery status
- This is the Android Studio source project, **not a compiled APK**.
- The app is configured for Android SDK 35, Java 17, Kotlin 2.0.21 and Android Gradle Plugin 8.7.3.
- I have not built or tested an APK in an Android SDK environment in this session.
- Farm images are bundled category illustrations, not screenshots of exact farm builds.
- Tutorial URLs are targeted YouTube searches. Creator names are suggested research leads, not verified authorship claims. The app labels these limits instead of pretending all 83 entries have been audited.
- Materials are planning estimates, not exact build counts. Follow the exact tutorial/schematic for quantities.
- Some recent-content entries are research projects rather than confirmed renewable farms.

## Build an APK (Windows)
1. Install Android Studio from https://developer.android.com/studio
2. Open Android Studio → **Open** → choose the extracted `CraftFarmAndroid` folder.
3. Allow Gradle sync and install Android SDK Platform 35 if prompted.
4. Set Gradle JDK to JDK 17 (Android Studio's embedded JDK is usually suitable).
5. Select **Build → Build Bundle(s) / APK(s) → Build APK(s)**.
6. When complete, click **locate** in the notification. The debug APK is usually at:
   `app/build/outputs/apk/debug/app-debug.apk`
7. Transfer that APK to your Android phone, open it, and allow installation from that source if Android asks.

## Build from command line
From this directory, with Android SDK configured and Gradle installed:
`gradle assembleDebug`
The output path is the same. This project does not bundle the Gradle wrapper JAR; Android Studio can sync/build it, or you can generate a wrapper with `gradle wrapper`.

## App features
- Farm library with stage, search, automation filter and completion checkboxes
- Tutorial search and design-lead fields
- Version notes and caveats
- Local offline farm data and category illustrations
- Build queue, materials checklist, per-farm notes
- Achievements and progress statistics
- JSON backup export/import
- External links open in the phone browser

## Privacy
The app does not implement an account or cloud backend. Farm progress stays in local app storage. Internet permission is used only for opening external web links; the farm library and visuals are bundled.


## Optional: build the APK in GitHub Actions (without installing Android Studio)
This repository includes `.github/workflows/build-apk.yml`.
1. Create a new GitHub repository and upload/push the contents of this folder to its `main` branch.
2. Open the repository's **Actions** tab and select **Build CraftFarm APK**.
3. Click **Run workflow** if it has not run automatically after your push.
4. Open the successful run, scroll to **Artifacts**, and download `CraftFarm-debug-apk`.
5. Extract the downloaded artifact ZIP; it contains `app-debug.apk`. Transfer it to your Android phone and install it.

This workflow builds a debug APK, not a Play Store release. The APK is unsigned for Play Store distribution, but debug builds are signed with Android's debug key for local installation. GitHub account/repository setup and the first upload still need to be done by you; I cannot access your GitHub account or trigger its workflow from this chat.
