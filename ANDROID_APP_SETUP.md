# ANDROID_APP_SETUP.md

## How to Build and Compile Android APK

This document provides multiple methods to build and compile an Android APK for the project.

### Method 1: Building with Android Studio

1. **Install Android Studio**:
   - Download and install Android Studio from the [official site](https://developer.android.com/studio).

2. **Open the Project**:
   - Launch Android Studio and open the project folder.

3. **Configure the SDK**:
   - Ensure that you have the required Android SDK versions by navigating to `File > Project Structure > SDK Location`.

4. **Build the APK**:
   - Go to `Build > Build Bundle(s) / APK(s) > Build APK(s)`.
   - After the build completes, you will be notified via a notification bar.

5. **Locate the APK**:
   - The APK file can be found in `app/build/outputs/apk/debug/`.

### Method 2: Using APKTool

1. **Install APKTool**:
   - Download APKTool from the [official site](https://ibotpeaches.github.io/Apktool/).

2. **Decompile the APK (if necessary)**:
   - Open a terminal and run:
     ```bash
     apktool d your_apk_file.apk
     ```

3. **Modify the Code**:
   - Make any changes to the app's code (Java files, resources, etc.).

4. **Recompile the APK**:
   - Run the following command:
     ```bash
     apktool b your_apk_folder
     ```

5. **Sign the APK**:
   - Sign the APK using jarsigner or another signing tool.

### Method 3: Automated Building using GitHub Actions

1. **Set Up GitHub Actions**:
   - Create a `.github/workflows` directory in your repository if it doesn't exist.

2. **Create a Workflow YAML File**:
   - Create a file named `build.yml` and add the following example configuration:
     ```yaml
     name: Build APK

     on:
       push:
         branches:
           - main

     jobs:
       build:
         runs-on: ubuntu-latest

         steps:
         - name: Checkout code
           uses: actions/checkout@v2

         - name: Set up Java
           uses: actions/setup-java@v2
           with:
             java-version: '11'

         - name: Build APK
           run: ./gradlew build
     ```

3. **Trigger the Build**:
   - Push changes to the main branch to trigger the build process.

4. **Locate the APK**:
   - After the build process completes, you can find the APK in the artifacts generated from the workflow.

### Conclusion

Choose the method that best suits your development style. For ease of use and integration, Android Studio is recommended, while APKTool provides advanced customization opportunities and GitHub Actions offers a streamlined automated building process.