This tests using `GameActivity` with egui, winit and wgpu.

This is based on a re-worked winit backend here:
https://github.com/rib/winit/tree/android-activity

```
export ANDROID_NDK_HOME="path/to/ndk"
export ANDROID_HOME="path/to/sdk"

rustup target add aarch64-linux-android
cargo install cargo-ndk

cargo ndk -t arm64-v8a -o app/src/main/jniLibs/  build
./gradlew build
./gradlew installDebug
adb shell am start -n co.realfit.agdkeframe/.MainActivity
```

or use Docker:
```
docker build -t agdk-frame-build .
docker run --rm -it agdk-frame-build
docker cp <container id>:/home/android/app/build/outputs/apk/debug/app-debug.apk .
```

Notes: 
- sliding with spacebar only updates cursor after you've done sliding (should keep updating pposition while sliding)
- locking the screen while typing and unlocking the screen hides keyboard but the cursor is still present
- when rotated in landscape mode, keyboard doesn't pop out
- cursor is too large when editing in Code Editor demo