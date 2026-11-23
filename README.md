# NUMORA — Mental Arithmetic Training

An offline-first adaptive mental-maths trainer designed for RBI Grade B Phase I practice. The Android app wraps a self-contained HTML/JavaScript training experience in a native Android WebView.

## What is included

- **Brand and interface:** NUMORA Swiss Edition identity, warm-white / graphite palette with vermilion and restrained blue accents, editorial typographic hierarchy, spacious modular grid, subtle micro-interactions, SVG/vector graphics, and four clear destinations: Practice, Progress, Rewards, Settings.
- **Practice:** Intermediate, Advanced and Pro tiers; Mixed and focused topic sessions; 10, 15 or 20-question sprints; timed answers, skips, quick-method explanations and end-of-session review.
- **Adaptive coach:** Per-skill accuracy, recent performance, response time, slow-answer patterns, error debt, difficulty offsets, and spaced review scheduling. Mixed practice weights weak and due skills more heavily.
- **Long-term memory:** Local persistence for the learning model, recent answers, up to 2,500 detailed answer events, up to 12,000 exact question keys, daily activity, streaks and up to 100 recent sprint records.
- **Rewards:** XP, coins, levels, daily missions, streaks and six milestone badges.
- **Backup:** Export and restore the full learning profile as JSON. Older RBI Mental Maths backup files are accepted and normalized.
- **Reminders:** Optional Android notification reminders approximately every three hours. Delivery can be delayed by Android battery management.
- **Offline:** No login, remote database, analytics SDK, font CDN or other network dependency in the practice app.

## Build the APK with GitHub Actions

This is the easiest route; Android Studio is not required.

1. Download and extract this project ZIP on a computer.
2. Open your GitHub repository, or create a new one.
3. Upload the **contents** of this extracted folder to the repository's `main` branch. Do not upload one extra enclosing folder.
4. Confirm the workflow file is at exactly `.github/workflows/build-apk.yml` (`.github` starts with a dot; `workflows` does not).
5. Open **Actions** and select **Build NUMORA Android APK**.
6. Wait for the run to complete successfully, then open it and download the artifact `numora-android-debug-apk`.
7. Extract the downloaded artifact ZIP. It contains `app-debug.apk`.
8. Transfer `app-debug.apk` to your OnePlus 12 and install it. Allow your file manager to install unknown apps when Android asks.

A push to `main` also starts the same build automatically.

## Install an update without losing your local profile

The application ID deliberately remains `com.archeepal.rbimentalcoach`, the same as the previous RBI Mental Maths build. The version is incremented to `2.1.0` / version code `4`. Export a JSON backup from Settings in the previous app before installing this build. Try installing over the existing app first. If Android reports a signature conflict, uninstall the old app only after exporting, install this build, and restore the JSON backup. A debug APK is not a stable production-signing identity.

## Build tooling

Pinned to current stable versions verified for this project as of 24 November 2026:

- Android Gradle Plugin **9.5.0**
- Gradle **9.9.2**
- JDK **17** (the AGP 9.5 default/minimum)
- Android SDK Platform **36** and Build Tools **36.0.0**
- AndroidX WebKit **1.18.0**
- GitHub Actions: checkout **v7.0.1**, setup-java **v6.3.0**, setup-android **v4.0.4**, setup-gradle **v6.4.1**, upload-artifact **v7.0.2**

Versions are pinned rather than using dynamic `+` dependencies. See the official release sources linked below for current version details.

## Data and privacy

The training profile is stored in WebView local storage under the app's stable `https://appassets.androidplatform.net/assets/index.html` origin. The app can run offline and does not send practice data to a server. Export your profile before uninstalling, clearing app storage or changing phones; Android normally removes local app data on uninstall.

## Reminder behaviour

The reminder starts about three hours after the switch is enabled and schedules the next reminder after delivery. It uses an inexact, battery-aware Android alarm; OnePlus/Android power management can defer delivery. Allow notifications when prompted. The reminder is optional.

## Technical limitations

- The included workflow builds a debug-signed APK for personal sideloading. It is not a Play Store production release and is not signed with a private release key.
- Browser preview (`PREVIEW.html`) includes practice, local memory and rewards, but Android-only reminder and native document-picker behaviour require the installed app.
- Exact seen-question avoidance is best-effort after the available question space has been exhausted, particularly for finite recall patterns.

## Project layout

- `app/src/main/assets/index.html` — complete offline app UI and question/adaptive/reward engine.
- `app/src/main/java/...` — native WebView host, reminder receiver, reboot receiver and backup bridge.
- `app/src/main/res/drawable/` — NUMORA launcher and notification vector artwork.
- `.github/workflows/build-apk.yml` — reproducible APK build pipeline.
- `PREVIEW.html` — openable desktop/mobile browser preview.
- `INSTALL-ONEPLUS-12.txt` — compact install guide.


## Official version references

- Android Gradle Plugin 9.5 release notes: https://developer.android.com/build/releases/agp-9-5-0-release-notes
- Android Gradle Plugin API reference: https://developer.android.com/reference/tools/gradle-api
- Gradle releases: https://gradle.org/releases/
- Android SDK platform release notes: https://developer.android.com/tools/releases/platforms
- AndroidX WebKit releases: https://developer.android.com/jetpack/androidx/releases/webkit
- GitHub Actions releases: https://github.com/actions/checkout/releases, https://github.com/actions/setup-java/releases, https://github.com/actions/upload-artifact/releases
- Gradle Actions releases: https://github.com/gradle/actions/releases
- Android SDK setup action: https://github.com/android-actions/setup-android/releases


## Visual system — Swiss edition

The interface uses a restrained Swiss-inspired visual system: warm white surfaces, near-black typography, one vermilion signal colour, a measured blue for analytical feedback, a consistent spacing scale, sharp modular alignment, and generous whitespace. Decorative gradients and oversized rounded cards have been removed. Motion is limited to small state transitions and question/feedback entrance cues; reduced-motion settings are respected.
