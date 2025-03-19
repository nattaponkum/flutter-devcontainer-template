# Flutter Dev Container for Android

This project provides a pre-configured development container for building Flutter applications in Android.

## Getting Started

1. **Open in Dev Container:** Open this project in VS Code and allow it to open in a Dev Container. This will build the Docker image and start the container.

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
> You can also use this devcontainer with other IDEs using [DevPod(https://devpod.sh/). It's free and open source!
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
