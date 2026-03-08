# Assignment TP1 - System Info App (Continuation of Android Studio)

**Course:** Mobile Application Development (DAM)  
**Student:** Marta Garcia (nº 51564)  
**Date:** 2026-03-08  
**Repository URL:** https://github.com/martapg15/DAM_SystemInfoApp

---

## 1. Introduction
This assignment consists of building a simple Android application that displays information about the current device build. The goal is to practice Android Studio basics, working with XML-based layouts, and reading system properties through the Android framework.

According to the requirements, the application must show device build information inside a **MultiLine Text widget**, extracting values from the `android.os.Build` object.

## 2. System Overview
The app presents a single screen containing a multiline text field that is automatically filled with system/build information when the app starts.

Displayed information includes:
- Manufacturer, model, brand, type, user
- Android version details (SDK level, release)
- Build display and incremental version

Main use case:
- **View device information:** the user opens the app and immediately sees the device build data presented as multiline text.

## 3. Architecture and Design
### Architecture
- Single-activity Android app using **`AppCompatActivity`**.
- UI is defined in XML (`activity_main.xml`), while data is loaded and displayed in `MainActivity.kt`.

### Folder structure (high-level)
- `app/` Android application module (source + resources)
- `gradle/` Gradle wrapper/config files
- Root Gradle files (`build.gradle.kts`, `settings.gradle.kts`, etc.)

### Design choices
- A single **read-only multiline `EditText`** is used to display the information (made non-focusable and with cursor disabled).
- Device properties are obtained using `android.os.Build` and `Build.VERSION`.

## 4. Implementation
### MainActivity (core logic)
In `MainActivity.kt`, the app:
- Loads the layout with `setContentView(R.layout.activity_main)`.
- Retrieves the multiline `EditText` with `findViewById`.
- Builds a formatted text block using properties from `Build` and `Build.VERSION`.
- Sets the resulting string into the `EditText` using `setText`.

Fields included in the output:
- `Build.MANUFACTURER`, `Build.MODEL`, `Build.BRAND`, `Build.TYPE`, `Build.USER`
- `Build.VERSION.SDK_INT`, `Build.VERSION.RELEASE`
- `Build.DISPLAY`, `Build.VERSION.INCREMENTAL`
- `Build.VERSION_CODES.BASE` (base API constant)

### Layout (XML views)
`activity_main.xml` defines:
- A root `ConstraintLayout`
- One multiline `EditText` configured as non-editable (`focusable=false`, `cursorVisible=false`) to behave like a display widget.

## 5. Testing and Validation
Testing was performed manually using Android Studio by running the app on virtual devices:
- Verified that the app starts and displays device information immediately.
- Verified that the text is multiline and readable.
- Confirmed that the field is not editable (no cursor and no keyboard popup).

Known limitations:
- Output formatting is fixed and not customizable in the UI.
- The screen is very simple (no copy/share button and no dynamic refresh).

## 6. Usage Instructions
### Requirements
- Android Studio
- Android SDK installed  
- (Gradle configuration is the same style as the previous project.)

### Run instructions
1. Clone the repository:
   - `git clone https://github.com/martapg15/DAM_SystemInfoApp`
2. Open the project in Android Studio.
3. Let Gradle sync.
4. Run the `app` configuration on an emulator or a connected Android device.

---

# Development Process

## 12. Version Control and Commit History
The repository history reflects incremental work:
- Initial implementation of the System Info App (including project build files).
- Later validation/testing by running the application on different virtual devices.

## 13. Difficulties and Lessons Learned
- Learned how to use `android.os.Build` and `Build.VERSION` to extract device/build information safely.
- Practiced using a multiline text widget in XML and configuring an `EditText` to behave as a read-only display field.
- Reinforced understanding of the Android project structure and the importance of committing all required build/config files.

## 14. Future Improvements
- Replace the `EditText` with a more appropriate read-only UI (e.g., `TextView` inside a `ScrollView`) and improve formatting.
- Add a **copy/share** button to export the device information.

## 15. AI Usage Disclosure (Mandatory)
In this part of the assignment, the use of AI tools for code generation was explicitly forbidden ([AC YES, AI NO]). Therefore, all code in this repository was implemented manually by the student.

However, AI tools were used only to assist in revising and improving the wording of the README report, as permitted by the assignment guidelines. I remain fully responsible for the accuracy and content of this documentation.
