# Age Calc

Age Calc is a professional, offline Android age calculator built with **Java + XML only**.
This build launches **directly into MainActivity** (no splash screen) and ships a
**premium auto-generated launcher icon** as PNG mipmaps (easy to replace with MT Manager).

## Features
- Age calculation (years/months/weeks/days/hours/minutes/seconds) + live second counter
- Next birthday countdown, birthday info (zodiac, birthstone, generation, etc.)
- Time-passed stats, life statistics, leap-year detection
- Date difference + anniversary calculator + retirement calculator
- Saved profiles (local JSON), search, sort, export/import (TXT)
- Birthday reminders (notifications), light/dark theme, Material Design UI

## Build in GitHub Codespaces
1. Open repo in Codespaces, wait for SDK setup (or run `bash .devcontainer/setup-sdk.sh`).
2. **IMPORTANT (Java 17):** this project needs Java 17. If the default Java is newer
   (e.g. 25) Gradle 8.5 crashes with `IllegalArgumentException: 25.0.2`. The generator
   auto-detects a Java 17 install and writes `org.gradle.java.home`. If it still fails:
   ```bash
   export JAVA_HOME=$(ls -d /usr/lib/jvm/*17* | head -n1)
   export PATH=$JAVA_HOME/bin:$PATH
   echo "org.gradle.java.home=$JAVA_HOME" >> gradle.properties
   ```
3. Build (use `bash gradlew`, NOT `./gradlew`):
   ```bash
   bash gradlew clean assembleDebug --stacktrace --no-daemon
   ```
   APK: `app/build/outputs/apk/debug/app-debug.apk`

## Replace the icon with MT Manager (Banglish)
APK open korun MT Manager e -> `res/mipmap-mdpi/ ... res/mipmap-xxxhdpi/` -> prottek folder e
`ic_launcher.png` + `ic_launcher_round.png` apnar notun icon diye replace korun -> Save -> Sign -> Install.
(MT Manager er built-in "Icon edit" use korle auto hoye jabe.) Best: 512x512 / 1024x1024 square PNG.

## Troubleshooting
- `SDK location not found` -> run setup-sdk, then `echo "sdk.dir=$HOME/android-sdk" > local.properties`.
- `gradlew` CRLF -> `sed -i 's/\r$//' gradlew && chmod +x gradlew`.
- OutOfMemory -> lower `-Xmx` in `gradle.properties`.

## License
MIT
