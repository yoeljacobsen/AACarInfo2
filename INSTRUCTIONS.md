# INSTRUCTIONS.md: Android Auto EV Dashboard App - Setup and Usage

This document provides instructions for setting up the development environment, building, and running the Android Auto EV Dashboard application. Adherence to these instructions is crucial for a smooth co-development process.

## 1. Development Environment Setup

To develop this Android Auto application, you will need:

*   **Android Studio**: Download and install the latest stable version from the [official Android Developers website](https://developer.android.com/studio).
*   **Android SDK**: Ensure you have the necessary Android SDK platforms installed (API Level 30+ recommended for Android Auto development).
*   **Java Development Kit (JDK)**: Android Studio typically bundles a compatible JDK. Verify it's correctly configured.
*   **Git**: For version control. Ensure it's installed and configured on your system.

### 1.1 Clone the Repository

```bash
git clone <repository_url>
cd AACarInfo2
```

### 1.2 Open Project in Android Studio

1.  Launch Android Studio.
2.  Select `Open an existing Android Studio project`.
3.  Navigate to the cloned `AACarInfo2` directory and select it.

Android Studio will automatically sync Gradle files and set up the project.

## 2. Building the Application

### 2.1 Build from Android Studio

1.  In Android Studio, go to `Build > Make Project` or click the hammer icon in the toolbar.
2.  This will compile the application and generate the APKs.

### 2.2 Build from Command Line

Navigate to the project root directory (`AACarInfo2/`) in your terminal and run:

```bash
./gradlew assembleDebug
```

This command will build the debug APK. The output APK will be located in `app/build/outputs/apk/debug/`.

## 3. Running the Application

### 3.1 Running on an Android Device/Emulator

For the phone-side application:

1.  Connect an Android device with USB debugging enabled or start an Android Emulator.
2.  In Android Studio, select your target device/emulator from the dropdown menu in the toolbar.
3.  Click the `Run` (green play) button.

### 3.2 Running on Android Auto Desktop Head Unit (DHU)

To test the Android Auto integration, you'll need the Desktop Head Unit (DHU).

1.  **Install DHU**: Follow the instructions on the [Android Developers website](https://developer.android.com/training/cars/auto/testing#dhu) to install and set up the DHU.
2.  **Enable Developer Mode on Phone**: On your Android phone, go to `Settings > About phone` and tap `Build number` seven times to enable Developer options. Then, in Developer options, enable `Android Auto developer mode`.
3.  **Run App on Phone**: Install the app on your phone as described in 3.1.
4.  **Connect to DHU**: Connect your phone to your computer via USB. Open a terminal and run:
    ```bash
    adb forward tcp:5277 tcp:5277
    ```
5.  **Start DHU**: Launch the DHU from your SDK installation directory (e.g., `~/Android/Sdk/extras/google/auto/`).
    ```bash
    ./desktop-head-unit
    ```
    The DHU will simulate an Android Auto head unit, and your app should appear in the launcher.

## 4. Co-development Workflow

As per the AGILE-AI Protocol (`SPEC.md`):

*   **PLAN MODE**: When a new task is assigned, the AI agent will first propose a plan. Review and approve this plan before proceeding.
*   **ACT MODE**: The AI agent will then execute the plan, following the Red-Green-Refactor-Reflect (RG-RR) cycle. Monitor its progress, review code changes, and provide feedback as needed.
*   **Debugging**: Refer to `DEBUGGING.md` for the structured debugging protocol.

By following these instructions, you can effectively set up your environment and participate in the co-development of the Android Auto EV Dashboard application.
