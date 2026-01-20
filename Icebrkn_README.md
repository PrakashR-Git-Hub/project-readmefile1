# ICEBRKN iOS

## Table of Contents

- [Overview](#overview)
- [Core Features](#core-features)
  - [Data Cleansing](#data-cleansing)
  - [Data Verification](#data-verification)
  - [Dossier Creation](#dossier-creation)
  - [Community-Enriched Profiles](#community-enriched-profiles)
- [Subscription Plans](#subscription-plans)
- [Pricing](#pricing)
  - [Monthly Plan](#monthly-plan)
  - [Yearly Plan](#yearly-plan)
- [Getting Started](#getting-started)
- [Development Requirements](#development-requirements)
- [Configuration](#configuration)
  - [Schemes](#schemes)
  - [Environment Files](#environment-files)
- [Project Structure](#project-structure)
  - [Common](#common)
  - [Modules](#modules)
  - [Resources](#resources)
  - [API](#api)
- [In-App Purchases](#in-app-purchases)
- [Third-Party Services & SDKs](#third-party-services--sdks)
  - [Google Contacts (Gmail)](#google-contacts-gmail)
  - [Microsoft Outlook Contacts](#microsoft-outlook-contacts)
  - [Apple iCloud Contacts](#apple-icloud-contacts)
- [Firebase Integration](#firebase-integration)
  - [Firebase Authentication](#firebase-authentication)
  - [Firebase Crashlytics](#firebase-crashlytics)
- [Security & Data Protection](#security--data-protection)
- [Infrastructure & Safety](#infrastructure--safety)
- [Deployment](#deployment)
  - [App Store Distribution](#app-store-distribution)
- [Backend API](#backend-api)
- [License](#license)

## Overview

ICEBRKN is a purpose-driven networking platform that helps individuals connect through accurate, verified, and enriched information. The iOS application enables users to import contacts from multiple sources, cleanse and deduplicate data, and generate rich profile dossiers that provide meaningful insights into people within their network.

Users can seamlessly synchronize contacts from **Gmail**, **iCloud**, and **Outlook**, after which ICEBRKN intelligently removes duplicates and inconsistencies to maintain a single source of truth. Every imported contact is transformed into a structured **profile dossier**, enabling deeper understanding, trust, and purposeful connections.

ICEBRKN is designed for users who value data integrity, professional credibility, and authentic engagement — whether for personal networking, professional collaboration, or data validation.

Try ICEBRKN for free or unlock its full potential with premium features.

---

## Core Features

### Data Cleansing
ICEBRKN uses advanced algorithms to eliminate duplicate, inconsistent, and outdated contact data across multiple sources. This ensures a clean, reliable, and unified contact list that reflects accurate information at all times.

### Data Verification
Premium users can verify the authenticity and accuracy of profile data, creating a trusted foundation for meaningful and reliable connections.

### Dossier Creation
Users can build comprehensive personal and professional profiles that showcase their complete digital and social footprint. Dossiers include personal details, career information, and lifestyle attributes — all in one place.

### Community-Enriched Profiles
Profiles can be enhanced through community contributions, providing diverse perspectives and deeper insights. This collaborative approach helps users understand others beyond surface-level information and strengthens community trust.

---

## Subscription Plans

Unlock the full potential of ICEBRKN with flexible subscription options.

| Feature | Free | Premium |
|------|------|---------|
| Contact Cleansing | Yes | Yes |
| Contact Data Enrichment | Yes | Yes |
| Data Verification | No | Yes |
| Suggest Profile Edits | No | Yes |
| Profile Enrichment Requests | No | 10 / month |
| Invitations | 15 / month | Unlimited |
| Profile Dossier Access | Limited | Full |

---

## Pricing

### Monthly Plan
**$9.99 / month**  
Gain full access to ICEBRKN’s premium features.

### Yearly Plan
**$109.99 / year**  
Equivalent to **$9.17 per month** — save more with an annual subscription.

---

## Getting Started

1. Install **Xcode 15.0 or later** on your Mac.
2. Clone or download the project repository.
3. Open the `.xcworkspace` file in Xcode.
4. Review the project structure and configurations.
5. Select a build scheme: **Dev**, **QA**, **Staging**, or **Live**.
6. Build and run the project on a simulator or physical device.

---

## Development Requirements

- **Xcode:** 15.0+
- **iOS Deployment Target:** iOS 13+
- **Language:** Swift 5.9+
- **CocoaPods:** 1.10.1
- **macOS:** Catalina 10.15.4+

---

## Configuration

### Schemes

The project supports multiple environment schemes:

- Dev
- QA
- Staging
- Live

Switch schemes directly from Xcode to change environments.

### Environment Files

Environment-specific configurations are located at:

```
ProjectFolder/EnvironmentConfiguration
```

Refer to `Environment.swift` for environment variable setup and usage.

---

## Project Structure

The project follows the **MVVM (Model–View–ViewModel)** architecture pattern.

### Common
Shared resources used throughout the app:
- Utility classes and extensions
- Global constants and enums
- Reusable UI components (buttons, loaders, alerts)

### Modules
Feature-based modular structure. Each module typically contains:
- **Views:** UI components (UIViewController, SwiftUI views, Storyboards/XIBs)
- **ViewModels:** Presentation logic and state handling
- **Models:** Feature-specific data models

### Resources
Static assets and resources:
- Images, fonts, and colors
- Asset catalogs (`.xcassets`)
- Audio, video, or mock JSON files

### API
Networking and backend communication:
- API routes and endpoints
- Alamofire-based HTTP clients
- Response parsing and error handling

---

## In-App Purchases

ICEBRKN supports iOS In-App Purchases for premium feature access.

### Setup Notes

- Sign in to Xcode using the correct Apple Developer account.
- Enable **In-App Purchase** capability in target settings.
- Define products in **App Store Connect**.
- Purchases are handled using **StoreKit**.
- Restore purchases is supported.
- Use **Sandbox Apple IDs** for testing.

⚠️ Product identifiers are case-sensitive and must exactly match App Store Connect.

---

## Third-Party Services & SDKs

### Google Contacts (Gmail)
- Uses **Google People API** via REST
- OAuth 2.0 authentication and consent flow
- Imports and syncs Gmail contacts

### Microsoft Outlook Contacts
- Authentication via **MSAL**
- Contacts fetched using **Microsoft Graph API**
- Secure token management

### Apple iCloud Contacts
- Uses **Contacts.framework (NSContacts)**
- Accesses local and iCloud-synced contacts
- Requires system-level user permission

## Firebase Integration

### Firebase Authentication
- Phone number authentication using OTP
- Secure and scalable user authentication

### Firebase Crashlytics
- Automatic crash reporting
- Non-fatal error logging
- Enabled on app launch

---

## Security & Data Protection

- Secure storage using **Keychain Services** for:
  - Authentication tokens
  - Encrypted user data
  - Session identifiers
- All data is sandboxed and securely persisted across app launches

---

## Infrastructure & Safety

- Backend infrastructure hosted on **AWS**
- Scalable and highly available architecture
- Community safety tools and structured reporting mechanisms

---

## Deployment

### App Store Distribution

1. Select the appropriate **Release scheme** in Xcode.
2. Navigate to **Product > Archive**.
3. Validate the archive using **Organizer**.
4. Distribute the app via:
   - **App Store Connect** for App Store submission
   - **Ad Hoc** or **Enterprise** for internal distribution
5. Ensure correct provisioning profiles and certificates are selected.
6. Upload the build to App Store Connect or export the IPA.

---

## Backend API

- Communication via **REST APIs**
- Networking powered by **Alamofire**
- Refer to the **Backend API Reference** for endpoint documentation

---

## License

© ICEBRKN. All rights reserved.
