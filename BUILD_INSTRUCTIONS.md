# Build Instructions (simple)

## Run the app (no signing needed)
1. Install Android Studio (latest stable). It includes JDK 17 and can install Android SDK 36.
2. Unzip `KhataPro_Phase1_Updated.zip`.
3. Android Studio > File > Open > choose the `KhataPro` folder. Wait for "Gradle sync" (needs internet).
   If Studio asks to install SDK Platform 36 or accept licenses, accept.
4. Connect a phone with USB debugging, or start an emulator, then press the green Run button.
5. If Sync or Build shows red errors, copy the exact message and send it to Claude.

## Run tests
- JVM unit tests: right-click `app/src/test` > Run Tests (or `./gradlew testDebugUnitTest`).
- Device tests (database rules): right-click `app/src/androidTest` > Run (needs emulator/phone).

## Release APK / AAB (later, when the app is finished)
1. Create a key once: Build > Generate Signed App Bundle or APK > Create new keystore. Store the `.jks`
   file OUTSIDE this folder and back it up. If you lose it you cannot update the app.
2. Or create `keystore.properties` in the project root (it is git-ignored):
   storeFile=/full/path/key.jks / storePassword=... / keyAlias=... / keyPassword=...
3. Run `./gradlew assembleRelease bundleRelease`.
Never upload the keystore or passwords to GitHub.

## About gradlew
`gradle/wrapper/gradle-wrapper.properties` is included (Gradle 8.11.1). The wrapper jar and `gradlew`
scripts could not be generated offline. Android Studio works without them. For command line use, run
`gradle wrapper --gradle-version 8.11.1` once.

If a library version is not found during Sync, update the version number in `app/build.gradle.kts`
or the root `build.gradle.kts` to the latest stable one.
