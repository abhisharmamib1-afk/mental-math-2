NUMORA — SWISS EDITION

A clean, modern mental-arithmetic training app for RBI Grade B Phase I.

DESIGN
- Swiss-inspired editorial hierarchy and modular layout
- Warm white / graphite palette with vermilion as the primary signal colour
- Generous whitespace, precise alignment, restrained 3–12px radii
- Small interaction transitions; respects reduced-motion preferences
- Functional practice, progress, rewards and settings destinations

FUNCTIONALITY
- Intermediate, Advanced and Pro question levels
- Mixed and focused skill filters
- 10 / 15 / 20-question sessions
- Answer checking, skip, timed response feedback and worked methods
- Adaptive skill memory, error debt and spaced review scheduling
- XP, coins, streaks, daily missions and achievement badges
- Local persistence, JSON export/import and Android three-hour reminders

BUILD APK
1. Upload the CONTENTS of this folder to the root of your GitHub repository.
2. Keep .github/workflows/build-apk.yml (the folder is named .github, then workflows).
3. Commit to main or run the workflow manually from GitHub Actions.
4. Wait for Build NUMORA Android APK to succeed.
5. Download the numora-android-debug-apk artifact and extract app-debug.apk.
6. Install app-debug.apk on your OnePlus 12.

APP ID
com.archeepal.rbimentalcoach (same ID as the previous version).

DATA NOTE
Before installing the updated APK, export a JSON backup from Settings in the old app. Try installing over the existing app first. If Android reports a signature conflict, uninstall only after exporting, then install the new APK and restore the JSON backup.
