# AgriOne Digital Twin Platform

Welcome to the AgriOne Digital Twin Platform repository. This is an enterprise-level agriculture production intelligence platform built to monitor, manage, and optimize vineyard operations using real-time IoT metrics, satellite data, and AI-driven agronomy support.

## Repository Architecture

This mono-repo is organized into two primary project environments, split by platform delivery:

### 1. Web (`/web`)
The `web` directory holds the core infrastructure for the browser-based platform and the system's central backend services.

- **Frontend (`/web/agritechplatform`)**: An Angular 17+ web application that serves as the central digital twin dashboard. It includes data visualization, map integrations, and the main user-facing tools.
- **Backend (`/web/backend`)**: A FastAPI Python service that functions as the central data engine for the *entire platform*. It handles database connections, proxying of the OpenRouter AI chat (Grower GPT), satellite metrics, and the main core business logic.

> **Note:** For specific setup instructions for either the Angular web client or the FastAPI backend, please see the [Web README](web/README.md).

### 2. Mobile (`/mobile`)
The `mobile` directory holds the companion mobile application.

- **Frontend (`/mobile`)**: A React Native application designed for iOS and Android deployment. 
- **Shared Backend Integration**: The mobile application does *not* have its own separate backend. It shares and connects to the same central FastAPI backend located in the `/web/backend` directory for data, authentication, and AI GPT services.

> **Note:** For specific environment setup, Metro bundler initialization, and deployment instructions for the React Native app, please see the [Mobile README](mobile/README.md).

---

## Quick Start & Setup Routing

To get the entire stack up and running locally, you generally want to set up components in the following order:

1. **Setup the Backend Engine:** Navigate to `web/backend` and start the FastAPI service. (This is required for both the web app and the mobile app to function fully).
2. **Setup the Web Dashboard:** Navigate to `web/agritechplatform` to run the Angular application.
3. **Setup the Mobile Client:** Navigate to `mobile/` to boot the React Native application on your emulator or physical device.

Please refer to the respective sub-directory README files for the granular step-by-step installation guides!
