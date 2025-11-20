# 🧮 Modern Android Calculator

A sleek, professional calculator app built with **Android Studio (Kotlin & XML)**. It features a modern dark UI, persistent calculation history, and a custom **in-app auto-update system** powered by GitHub.

## ✨ Features

* **Standard Arithmetic:** Addition, Subtraction, Multiplication, Division.
* **📝 Persistent History:**
    * Saves calculations automatically using `SharedPreferences`.
    * History remains even after closing the app.
    * Beautiful card-based UI for history items.
    * "Clear History" functionality.
* **🎨 Modern UI:**
    * Professional Dark Theme.
    * Responsive layout using `LinearLayout` weights (works on all screen sizes).
    * Custom rounded buttons and vector icons.
* **🔄 Self-Updating System:**
    * Checks a remote GitHub repository for updates.
    * Automatically downloads and installs the new APK if a newer version is detected.

## 🛠️ Tech Stack

* **Language:** Kotlin
* **UI:** XML (Linear Layouts, ScrollViews)
* **Asynchronous:** Kotlin Coroutines (for background network checks)
* **Storage:** SharedPreferences (for saving history data)
* **Networking:** Java `java.net.URL` for raw file reading
* **File Handling:** Android FileProvider (for secure APK installation)

## 🚀 How the Auto-Update Works

This app bypasses the Play Store for updates by acting as its own installer.

1.  **Version Check:** On startup, the app checks a raw `version.txt` file hosted on this GitHub repository.
2.  **Comparison:** It compares the online version number with the internal `CURRENT_VERSION` constant.
3.  **Download:** If an update is available, it downloads `app.apk` from the repository using `Coroutines`.
4.  **Install:** It triggers the Android Package Installer using a `FileProvider` to update the app seamlessly.

### Configuration for Updates
To push an update to users:
1.  Increment `CURRENT_VERSION` in `MainActivity.kt`.
2.  Generate a **Signed Release APK**.
3.  Rename the file to `app.apk` and upload it to the repo.
4.  Update `version.txt` in the repo to match the new version number.

## 📥 Installation

1.  Go to the [Releases](../../releases) page (or download `app.apk` from the root).
2.  Install the APK on your Android device.
3.  *Note: You may need to allow "Install from Unknown Sources" for the first install.*

## 🔧 Setup for Developers

1.  Clone the repository:
    ```bash
    git clone [https://github.com/justtheguyak/MyCalculatorUpdate.git](https://github.com/justtheguyak/MyCalculatorUpdate.git)
    ```
2.  Open the project in **Android Studio**.
3.  Sync Gradle files.
4.  **Important:** To test the update feature locally, you must generate a Signed APK. Debug builds may conflict with Release builds installed from GitHub due to signature mismatches.

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
