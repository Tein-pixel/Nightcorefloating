# NightcoreFloating

NightcoreFloating is an Android project distributed in this repository as the `NightcoreFloating.zip` source archive. GitHub Actions extracts that archive, builds a debug APK, and publishes the APK as a workflow artifact and GitHub Release asset.

## Build an APK with GitHub Actions

1. Open the repository's **Actions** tab.
2. Select **Build APK**.
3. Select **Run workflow** to start a manual build.
4. Open the completed workflow run.
5. Download the **NightcoreFloating-APK** artifact and extract it to obtain the debug APK.

A push to `main` also starts the workflow when `NightcoreFloating.zip` or `.github/workflows/build-apk.yml` changes.

## Build environment used by CI

The current workflow configures:

- Ubuntu GitHub-hosted runner.
- Eclipse Temurin JDK 17.
- Android SDK platform 34 and Build Tools 34.0.0.
- Gradle 8.2.1.
- Android `assembleDebug` task.

The archive must contain a Gradle Android project. The workflow recognizes either `NightcoreFloating/settings.gradle` or `settings.gradle` at the archive's extracted root. It then expects the Android application module to produce an APK under `app/build/outputs/apk/debug/`.

## Outputs

- Actions artifact: `NightcoreFloating-APK`.
- Artifact retention: 30 days.
- Release tag format: `v6.<run number>`.
- Release asset: the generated debug APK.

The debug APK is intended for testing. It is not a Play Store release and should not be treated as a production-signed build.

## Troubleshooting

**“NightcoreFloating.zip not found”**  
Check that the archive exists at the repository root and that its filename is exactly `NightcoreFloating.zip`.

**“Gradle project not found”**  
Inspect the ZIP contents and make sure `settings.gradle` is at the archive root or inside the `NightcoreFloating/` directory.

**Build fails during dependency or SDK resolution**  
Open the failed Actions run, expand the failed step, and inspect the first Gradle or SDK error. The workflow log is more useful than the final generic “build failed” message.

For the longer device-installation walkthrough, see [SETUP_GUIDE.md](SETUP_GUIDE.md).
