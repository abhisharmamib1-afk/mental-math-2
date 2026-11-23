RBI MENTAL MATHS — ANDROID APP SOURCE PROJECT

WHAT THIS BUILDS
- Android app: RBI Mental Maths
- Application ID: com.archeepal.rbimentalcoach
- Minimum Android: Android 8.0 (API 26)
- Designed for modern Android phones, including OnePlus 12
- Offline-first: all practice questions and the question engine run on-device
- Persistent learning profile using Android WebView's localStorage on a stable app asset origin
- Adaptive performance model persisted between rounds and app restarts
- Three-hour reminder toggle in Settings (Android notifications permission required)
- Profile export/import using Android document picker

ADAPTIVE LEARNING DESIGN
1. Per-skill records track attempts, accuracy, exponentially weighted response time,
   recent misses, error debt, due-for-review time and a skill difficulty offset.
2. In Mixed practice, skill weights use low accuracy, recent errors, slow response time,
   review due status and limited exposure to new skills.
3. Incorrect/skipped/slow work increases an error debt so the next test intentionally
   revisits that area. Correct fast answers gradually reduce its priority.
4. Each skill can adjust one difficulty step up/down based on a rolling window.
5. Overall difficulty changes only after at least two rounds and 15 combined questions:
   strong accuracy + fast average advances; persistent low accuracy or very slow work
   reduces the tier. This avoids jumping difficulty after one lucky round.
6. Exact question prompts are remembered locally and avoided across sessions when possible.
   A finite recall bank can eventually exhaust its unique prompts; the app never repeats
   an exact prompt inside one round.

LOCAL DATA
- Practice data is stored on the device in the app's private WebView localStorage.
- No login, cloud account or analytics endpoint is used.
- Use Settings > Export JSON to create a backup.
- Use Settings > Import JSON to restore it on a new install/device.
- Uninstalling the app normally removes its local data. Export a backup first.

BUILD APK WITH ANDROID STUDIO (EASIEST LOCAL ROUTE)
1. Install Android Studio on a computer.
2. Unzip this project folder.
3. Android Studio > Open > select the unzipped folder named rbi-mental-maths-android.
4. Allow Gradle sync. Use JDK 17 or newer for Gradle if Android Studio asks.
5. If prompted, install Android SDK Platform 35 and Build Tools 35.
6. Select Build > Build Bundle(s) / APK(s) > Build APK(s).
7. The generated file is:
   app/build/outputs/apk/debug/app-debug.apk
8. Transfer app-debug.apk to your OnePlus 12.
9. Open the APK on the phone and approve Android's "Install unknown apps" prompt
   for the app you used to open the file. Then tap Install.
10. Open RBI Mental Maths. Grant notifications when asked. In Settings, turn on
    Three-hour practice reminders if you want them.

BUILD APK USING GITHUB ACTIONS (NO ANDROID STUDIO REQUIRED)
1. Create a new GitHub repository.
2. Extract this ZIP on a computer.
3. Upload the contents of this project folder to the repository's main branch,
   keeping the .github/workflows/build-apk.yml path.
4. Open the repository's Actions tab.
5. Select "Build RBI Mental Maths APK" and press "Run workflow" (a push to main
   also starts a build automatically).
6. When the workflow finishes successfully, open that run and download the
   artifact named rbi-mental-maths-debug-apk.
7. Extract the downloaded artifact ZIP. It contains app-debug.apk.
8. Transfer app-debug.apk to the OnePlus 12 and install it as described above.

IMPORTANT NOTES
- This project ZIP is source code for building an APK; it is not itself an APK.
- The APK produced by assembleDebug is a debug-signed APK suitable for personal
  sideload installation. It is not a Play Store release.
- The three-hour alarm is inexact and Android/OnePlus battery optimisation may
  delay reminders. Notifications require the user to grant permission.
- The current reminder starts three hours after enabling it and then reschedules
  itself. It is not a precise wall-clock schedule.


For a shorter step-by-step phone installation guide, read INSTALL-ONEPLUS-12.txt.
