# WINNY iOS


## Table of Contents

- [Overview](#overview)
- [Plans](#plans)
- [Getting Started](#getting-started)
- [Development Requirements](#development-requirements)  
- [Configuration](#configuration)
- [Structure](#structure)
- [In-App Purchases](#in-app-purchases)
- [Third-Party Services & SDKs](#third-party-services--sdks)
- [Deployment](#deployment)
- [API](#api)


## Overview

**Winny** helps you build your social health with conversations and life stories that forge deeper connections with your family and friends today.

### Core Features

1. Record and share **video or audio stories** with friends and family.
2. **Chat** with friends and family — including **video and audio calls** and **recorded stories** for deeper connections.

---

## Plans

| Plan                       | Price | Duration | Storage | Description                              |
| -------------------------- | ----- | -------- | ------- | ---------------------------------------- |
| **Free**                   | Free  | —        | 5 GB    | Winny Cloud storage for up to 5 GB       |
| **Premium (Half Yearly)**  | $59   | 6 Months | 50 GB   | More space for more stories              |
| **Standard (Half Yearly)** | $39   | 6 Months | 20 GB   | Moderate storage for your stories        |
| **Premium (Monthly)**      | $12   | 1 Month  | 50 GB   | Flexible monthly plan with large storage |

---

## Getting Started

1. Ensure **Xcode 15.0 or above** is installed on your Mac.
2. Download or clone the project repository.
3. Open the `.xcworkspace` file in **Xcode**.
4. Review the project structure and code.
5. Select the appropriate build scheme — **Dev**, **QA**, **Staging**, or **Live**.
6. Run the project using your selected scheme.

---

## Development Requirements

* **Xcode:** 15.0 or later
* **Platform:** iOS 13 or later
* **Language:** Swift 5.9+
* **Dependency Manager:** CocoaPods
* **macOS:** Catalina 10.15.4 or later

---

## Configuration

### Schemes

The project includes the following environment schemes:

* **Dev**
* **QA**
* **Staging**
* **Live**

> You can switch environments directly from the Scheme selector in Xcode.

### Environment Files

Environment configurations are located at:

```
ProjectFolder/EnvironmentConfiguration
```

Refer to `Environment.swift` for additional setup details.

---

## Structure

This project follows the **MVVM (Model–View–ViewModel)** architecture.

### Folder Overview

* **Common**

  * Shared utilities, extensions, global constants, and reusable UI components.
* **Modules**

  * Each feature/screen as an independent module with:

    * **Views** — UI (UIViewController, SwiftUI View, Storyboards/XIBs)
    * **ViewModels** — Presentation and state logic
    * **Models** — Data structures for each module
* **Resources**

  * App assets (images, fonts, audio, JSON mock data, `.xcassets`)
* **API**

  * Networking layer with endpoints, HTTP clients, and error handling.

---

## In-App Purchases

Winny supports **In-App Purchases (IAP)** via **StoreKit** for unlocking premium features.

### Setup Notes

* Ensure you are signed in with the correct **Apple Developer Account**.
* Enable **In-App Purchase capability** in project target settings.
* Products are defined in **App Store Connect**.
* Supports **purchase, restore, and validation** flows.
* Restoring purchases is supported for users reinstalling or switching devices.
* Use **Sandbox Apple IDs** for testing.

> ⚠️ Product identifiers are **case-sensitive** and must match App Store Connect exactly.

---

## Third-Party Services & SDKs

### Agora – Video & Audio Calling

* Enables real-time 1-on-1 video and audio calling.
* Handles channel creation, token authentication, and lifecycle events.
* Token-based authentication supported.
* Call status synced with Firebase Real-Time Database.

### Firebase Integration

#### 1. Firebase Real-Time Database

* Tracks live **video/audio call statuses** (incoming, ringing, accepted, ended).
* Lightweight JSON-based synchronization between users.

#### 2. Firebase Authentication

* Supports **phone number sign-in** via OTP.
* Provides secure and scalable user authentication.
* Token refresh handled automatically by Firebase SDK.

#### 3. Firestore (Cloud Firestore)

* Stores **chat history** with real-time synchronization.
* Typical structure:

  ```
  /conversations/{conversationId}/messages/{messageId}
  ```
* Indexed for fast queries and scalability.

#### 4. Firebase Crashlytics

* Captures crash logs and stack traces.
* Automatically starts on app launch and can log non-fatal issues.

#### 5. Firebase Analytics

* Tracks **user interactions and engagement**.
* Supports funnel tracking and session analysis.
* Logs events such as:

  * `video_call_started`
  * `chat_message_sent`

---

## Security & Confidential Data

* Uses **Keychain Access** for securely storing:

  * Tokens
  * Encrypted user data
  * Session identifiers
* Data persists securely across launches and is sandboxed per app.

---

## Infrastructure & Safety

* Hosted on **AWS** for reliability and scalability.
* Includes structured reporting and community safety mechanisms.

---

## Deployment

### App Store Deployment

1. Open the project in **Xcode** and select the desired **Release scheme**.
2. Go to **Product > Archive** to build and archive the app.
3. Use **Organizer** → **Validate App** to run preliminary checks.
4. Choose **Distribute App**:

   * For App Store submission → **App Store Connect > Upload**
   * For internal distribution → **Ad Hoc** or **Enterprise**
5. Select the correct provisioning profile and signing certificate.
6. Xcode will upload the IPA to App Store Connect or export it locally for Ad Hoc distribution.

---

## API

* Uses **REST API** for backend communication.
* Networking powered by **Alamofire**.
* For complete endpoint details, refer to the **Backend API Reference**.

---

**© Winny — Build deeper connections, one story at a time.**
