### Setup
Install / acquire the following
1. [Android NDK](https://developer.android.com/ndk/guides/setup.html#install)
2. Get an unrooted physical or virutal device running Froyo
### Compiling and Deploying
1.    Set up an NDK standalone toolchain to compile the exploit for your Android.
    ```bash
    SYSROOT=$NDK/platforms/android-2.2/arch-<arch>/
    $NDK/build/tools/make-standalone-toolchain.sh --toolchain=<name> --platform=android-8 --install-dir=<toolchain_dir>
    export PATH=<toolchain_dir>:$PATH
    export NDK_CC=<compiler_name>
    ```
    See the NDK docs for more details
1.    Compile the exploit
    ```bash
    git clone https://github.com/Purdue-ACM-SIGSAC/android-froyo-root.git
    cd android-froyo-root
    NDK_CC -o exploit exploit.c
    adb push exploit /data/local/tmp
    adb shell chmod 777 /data/local/tmp/exploit
    ```
### Running
    ```bash
    adb shell ./data/local/tmp/exploit root
    ```
    or
    ```bash
    adb shell ./data/local/tmp/exploit unroot
    ```
