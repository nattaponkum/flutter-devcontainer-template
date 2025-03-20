<p align="center">
<img src="imgs/logo.png" alt="Logo" style="display: block; margin: 0 auto; width: 25%">
</p>

# Flutter Dev Container for Android

This project provides a pre-configured development container for building Flutter applications in Android.

Runs on Windows (WSL2 recommended), MacOS (see note at the end) and Linux (at least in theory, please someone test it).

> [!IMPORTANT]
> The container currently builds for the amd64 architecture regardless of the host system due to compatibility issues with Apple Silicon chips.
> I will eventually investigate native architecture builds later, but for now this will do.

## Prerequisites

- Docker
- VSCode, or most VSCode forks, or DevPod and most IDEs (see later tip)
- Ability to read

## Getting Started

1. **Open in Dev Container:** Open this project in VS Code and allow it to open in a Dev Container. This will build the Docker image and start the container.

> [!NOTE]
> The first time is gonna take a while, depending on how fast your internet is. This is because the SDKs and tools that need to be downloaded are relatively large (5GB approximately).

2. **Connect your Android Device:**

    * Enable developer mode and Wireless debugging on your Android device.
    * Note your device's IP address.
    * Open a new terminal in VS Code.
    * Run the following command, replacing `YOUR_DEVICE_IP` with your device's IP:

        ```bash
        task connect-device -- YOUR_DEVICE_IP
        ```

        Follow the on-screen instructions.

3. **Verify Connection:**

    * Run `flutter doctor` in the terminal.
    * Confirm that a green checkmark appears next to "Connected device".

> [!TIP]
> You can also use this devcontainer with other IDEs using [DevPod](https://devpod.sh/). It's free and open source!
>
> **Important Note for Alternative IDEs:** Some IDEs might default to the `sh` shell instead of `bash`, which is the shell configured in this devcontainer. If you're using an IDE other than VS Code, please ensure your terminal is configured to use `bash` to avoid potential compatibility issues.

> [!WARNING]
> Currently only Wireless connection is supported.
> Android 10 and older devices, an extra step going through USB debugging, which is not yet fully supported.

## Included Tools and Features

* Flutter SDK
* Android SDK and Command Line Tools
* OpenJDK 17
* VS Code extensions for Flutter and Dart development
* Starship prompt
* Go Task
* Customizable .bashrc

That's it! You're now ready to start developing Flutter apps for Android in a consistent and isolated environment.

## Current issues

1. Macs with Apple Silicon chips are forced to use the amd64 builds.
2. On these devices, compiling the app via `flutter run` succeeds, and hot reloading appears functional. However, the build process initially displays the following error. I hope the native build (if it works) will make this go away.

    ```sh
    Caught exception: Couldn't poll for events, error = 4
    Error while receiving file changes
    net.rubygrapefruit.platform.NativeException: Couldn't poll for events, error = 4
        at net.rubygrapefruit.platform.internal.jni.AbstractNativeFileEventFunctions$NativeFileWatcher.executeRunLoop0(Native Method)
        at net.rubygrapefruit.platform.internal.jni.AbstractNativeFileEventFunctions$NativeFileWatcher.executeRunLoop(AbstractNativeFileEventFunctions.java:42)
        at net.rubygrapefruit.platform.internal.jni.AbstractFileEventFunctions$AbstractFileWatcher$1.run(AbstractFileEventFunctions.java:154)
    ```
