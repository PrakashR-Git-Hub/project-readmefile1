# VYBES iOS

## Table of Contents


- [Overview](#overview)
- [Getting Started](#getting-started)
- [Development Requirements](#development-requirements)  
- [Configuration](#configuration)
- [Structure](#structure)
- [In-App Purchases](#in-app-purchases)
- [FaceTec SDK](#facetec-sdk)
- [Third-Party Services & SDKs](#third-party-services--sdks)
- [Deployment](#deployment)
- [API](#api)

---

## Overview

Vybes is a video-first dating platform focused on transparency, efficiency, and security. It blends real-world connection with digital safety to foster genuine relationships.

Core Features

* Identity Verification using government ID
* FaceTec Biometric Security for facial recognition & liveness checks
* Video-First Dating and scheduling
* Daily Free Date Giveaways for Premium Users

In-App Purchases

* Implemented In-App Purchase (IAP) using StoreKit
* Supports subscription-based Premium Membership
* Handles purchase, restoration, and validation flows securely
* Enables unlocking premium features: full access, daily giveaways, and exclusive invites

FaceTec Integration

* Integrated FaceTec SDK for biometric authentication
* Performed 3D Liveness Detection and Face Matching
* Ensures users are real and present during verification
* Used for onboarding, identity verification, and ongoing user trust

Agora Integration

* Integrated Agora SDK for real-time video calling
* Enabled 1-on-1 video dates with high-quality, low-latency streaming
* Managed channel creation, token authentication, and call lifecycle events
* Customized UI/UX for smooth in-app video experiences

Security & Confidential Data

* Used Keychain Access to securely store sensitive user data
* Safely handled authentication tokens, user credentials, and verification status
* Ensured data is encrypted and protected even if the device is compromised


Firebase Integration

* **Firebase Real-Time Database: ** Used to track live video call status (e.g., ringing, ongoing, ended)
* **Firebase Authentication: ** Supports Email and Phone Number authentication for secure, flexible sign-in
* **Firestore: ** Stores chat history (excluding media files) with real-time sync and scalability
* **Firebase Crashlytics: ** Captures and reports crash logs for better debugging and stability
* **Firebase Analytics: ** Tracks user behaviour and engagement for performance insights and feature improvement

Infrastructure & Safety

* Hosted on AWS for reliability and scalability
* Structured reporting and clear community protection policies

Plans

* Free: Access to core features
* Premium: Full access, daily giveaways, and exclusive events


---

## Getting Started

1. Make sure you have **Xcode 15.0** or above installed on your computer.  
2. Download or clone the project repository.  
3. Open the `.xcodeproj` file in Xcode.  
4. Review the code to understand its structure and functionality.  
5. Select a scheme (`Dev`, `QA`, `Staging`, or `Live`) based on your environment.  
6. Run the project using the selected scheme.

---

## Development Requirements

- Xcode 15 or later  
- Platform: iOS 13 or later  
- Swift 5.9+  
- CocoaPods 1.10.1  
- macOS Catalina Version 10.15.4 or later

---

## Configuration

### Schemes

The project includes multiple build schemes for different environments:

- **Dev**
- **QA**
- **Staging**
- **Live**

To switch environments, change the scheme directly in Xcode.

### Environment Files

Environment-specific configurations are located in:

**Location:** `Project Folder/EnvironmentConfiguration`


For further setup, refer to the `Environment.swift` file inside the project.

### Encryption

The app uses **CryptoKit** to secure API requests and responses.  
If you need to **disable encryption** (e.g., for DEBUG), set the following flag:

```swift
ENCRYPTIONENABLESTATUS = false
```

⚠️ Ensure the backend is also updated accordingly to handle unencrypted traffic.

---

## Structure

This project follows the **MVVM (Model-View-ViewModel)** architecture. Below is an overview of the folder structure and its purpose:

- **Common**  
  Contains shared resources used across the entire app, such as:
  - Utility classes and extensions  
  - Global constants and enums  
  - Reusable UI components (e.g., custom buttons, loaders)

- **Modules**  
  Each feature or screen is separated into its own module. Inside a module, files are typically organized into:
  - `Views`: UI files (`UIViewController`, `SwiftUI View`, Storyboards/XIBs)  
  - `ViewModels`: Logic to handle presentation and state  
  - `Models`: Data structures specific to the module

- **Resources**  
  Contains static assets used by the app:
  - Images, colors, fonts  
  - Audio, video, or JSON mock data  
  - Asset catalogs (`.xcassets`)

- **API**  
  Code responsible for networking:
  - API endpoints and routes  
  - HTTP clients and request handlers  
  - Response parsing and error handling

---

## In-App Purchases

The app supports iOS In-App Purchases (IAP) for unlocking premium features.

Setup & Notes
* Make sure to sign in to your Apple ID in Xcode with the correct developer account.
* Enable In-App Purchase capability in the project’s target settings.
* Products are defined in App Store Connect.
* All purchases are handled via StoreKit.
* Restoring purchases is supported for users who reinstall or switch devices.
* For testing, use Sandbox Apple IDs.

⚠️ Product identifiers are case-sensitive and must match exactly with what’s set up in App Store Connect.

---

## FaceTec SDK

This project uses the FaceTec SDK for facial recognition and liveness detection.

Setup & Integration

* FaceTec SDK is integrated for secure and accurate face authentication.
* Includes 3D Liveness Detection and Face Matching.
* Make sure to include the appropriate FaceTec.framework and resources in the project.
* The SDK is initialized via `FaceTec.sdk.initialize(...)` before starting a FaceTec session.


Notes

* FaceTec UI can be customized to match the app’s branding.
* All biometric processing is done on-device for user privacy.
* Results are sent to the backend for additional validation.

⚠️ You must have a valid FaceTec developer account and license to run the SDK.

---

## Third-Party Services & SDKs

This project integrates several third-party services to support real-time features, secure authentication, crash monitoring, and data persistence.

### Agora – Video Calling

- **Purpose**: Enables 1:1 or group **video call functionality**.
- **Use Case**: Real-time communication between users.
- **Integration**:
  - The SDK handles video stream encoding, decoding, and real-time audio/video transport.
  - Call status is synced with Firebase Real-Time DB.
- **Notes**:
  - Ensure a valid **Agora App ID** is configured.
  - Token-based authentication is supported (if enabled on the backend).

---

### Firebase

#### 1. Firebase Real-Time Database

- **Purpose**: Tracks and manages **video call statuses** in real-time.
- **Use Case**:
  - Handles states like incoming, ringing, accepted, ended, etc.
- **Notes**:
  - Uses lightweight JSON-based syncing.
  - Syncs call-related status flags between caller and receiver.

#### 2. Firebase Authentication

- **Purpose**: Handles **user sign-up and sign-in** using **email** and **phone number**.
- **Integration**:
  - Supports OTP-based phone authentication via Firebase UI.
  - Provides secure, scalable authentication.
- **Notes**:
  - Token refresh is managed automatically by the Firebase SDK.

#### 3. Firestore (Cloud Firestore)

- **Purpose**: Stores **chat history** (excluding media).
- **Use Case**:
  - Persistent chat data between users.
  - Real-time sync of text messages.
- **Notes**:
  - Structure is typically:
    ```
    /conversations/{conversationId}/messages/{messageId}
    ```
  - Indexed for performance.

#### 4. Firebase Crashlytics

- **Purpose**: Captures **crash reports and stack traces** in real-time.
- **Use Case**:
  - Monitor stability issues across devices and OS versions.
- **Integration**:
  - Automatically starts with app launch.
  - Can be triggered manually to log non-fatal issues.

#### 5. Firebase Analytics

- **Purpose**: Tracks **user interactions** and app usage patterns.
- **Use Case**:
  - Funnel tracking, session duration, feature engagement, etc.
- **Integration**:
  - Logs custom events (e.g., video_call_started, chat_message_sent, etc.).
  - Integrates with Crashlytics and Google Ads for deeper insight.

---

### Keychain Access

- **Purpose**: Stores **confidential and sensitive data** securely.
- **Use Case**:
  - Tokens
  - Encrypted user info
  - Session identifiers
- **Notes**:
  - Data stored in Keychain persists across app launches and is sandboxed per app.
  - Uses Apple's built-in Keychain Services API.

---

## Deployment

Remember that deploying an iOS app to the App Store requires an active Apple Developer account.

1. Open your project in Xcode, switch to the desired scheme (typically a Release build), and go to the Product menu. Select Archive. This will build and archive your app.
2. Once the archive is created, Xcode will automatically open the Organizer window. Select your archive and click the Validate App button to run preliminary checks (e.g., entitlements, certificates, etc.).
3. After validation, click Distribute App. For App Store submission, select App Store Connect > Upload. If you’re distributing for testing (outside of TestFlight), choose Ad Hoc or Enterprise instead.
4. Follow the steps in the distribution assistant, including selecting the correct provisioning profile and signing the certificate. Xcode will package and optionally upload the IPA to App Store Connect.
5. If you selected App Store Connect, your app will be uploaded directly to App Store Connect and won’t give you a local IPA file. However, for Ad Hoc distribution, an IPA will be saved locally, which can be installed on devices using MDM or tools like Apple Configurator.

---

## API 

* We are using a REST API
* Refer to our [Backend API Reference](https://vybesapi.revyrie.co/docs) for detailed endpoints.
* For HTTP networking we are using [Alamofire](https://github.com/Alamofire/Alamofire) 
