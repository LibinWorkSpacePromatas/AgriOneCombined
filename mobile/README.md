# AgriOne Digital Twin - Mobile App

This directory contains the mobile application for the AgriOne Digital Twin platform, built using **React Native**.

## Prerequisites & Required Accounts

Before starting, make sure your development environment is fully set up for React Native:

- **Node.js**: v18 or higher
- **React Native CLI environment**: Follow the official [React Native Environment Setup Guide](https://reactnative.dev/docs/environment-setup) for your target platform.
  - **For Android Development**: Android Studio, Android SDK, and a configured Android Emulator (or physical device).
  - **For iOS Development** *(macOS required)*: Xcode, Command Line Tools, and CocoaPods.
- **OpenRouter Account**: If the mobile application queries the AI GPT services directly, ensure you have an API key from [OpenRouter](https://openrouter.ai/).

---

## Installation

1. Navigate to the mobile project root directory:
   ```bash
   cd mobile
   ```
2. Install npm dependencies:
   ```bash
   npm install
   ```
3. **(iOS Only)** Install CocoaPods dependencies. From the `mobile` directory, run:
   ```bash
   cd ios
   bundle install
   bundle exec pod install
   cd ..
   ```

---

## Configuration

If the mobile application connects to a local backend API (e.g., the FastAPI service in the `web` folder), ensure the backend is running.

- **Emulator Network Setup**: If your backend is running on `localhost`:
  - **iOS Simulator** can access it via `http://localhost:8000`.
  - **Android Emulator** needs to access it via `http://10.0.2.2:8000`.
- Update any API endpoint URLs or environment variables in the project's config files to point to the correct backend IP address or deployed API.

---

## Running the App

### Step 1: Start the Metro Bundler

Metro is the JavaScript build tool for React Native. Start it by running:
```bash
npm start
```
*Keep this terminal window open.*

### Step 2: Build and Run the App

Open a **new** terminal window, navigate to the `mobile` directory, and run the command for your target platform.

#### For Android:
```bash
npm run android
```
*(Note for Windows Users: If PowerShell blocks execution of `npx`, run `npx.cmd react-native run-android` or use the provided `run-android.cmd` script).*

#### For iOS:
```bash
npm run ios
```

---

## Troubleshooting

- **Caching Issues**: If you experience stale code or unexpected Metro errors, try resetting the Metro cache:
  ```bash
  npm start -- --reset-cache
  ```
- **Execution Policy (Windows)**: If npm scripts fail due to execution policies, run `Set-ExecutionPolicy Unrestricted -Scope CurrentUser` in PowerShell as Administrator.
- **Dependencies out of sync**: If you recently pulled new changes, run `npm install` (and `cd ios && pod install` for iOS) to ensure native dependencies are up to date.
