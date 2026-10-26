# MilkCheque

Android prototype for a shared-table dining experience: browse a digital menu, build a cart, place an order, and review customer orders within a session.

Built with **Kotlin, Jetpack Compose, Retrofit, and Hilt**. This repository contains the Android client; menu, session, order, and payment operations depend on a separate backend.

## What the code includes

- Digital menu and item-detail screens.
- Cart quantity controls and subtotal, service-charge, and tax calculations.
- QR scanning and a session-start flow.
- Session order submission and an order-review screen.
- Customer selection and a payment-request flow that receives a URL from the backend.

The shared-bill payment flow is a prototype. It should not be treated as a complete, verified payment or settlement system.

## Architecture

| Area | Responsibility |
| --- | --- |
| `presentation/` | Compose screens, navigation, ViewModels, and UI state |
| `domain/` | Models, repository interfaces, and use cases |
| `data/` | Retrofit API, DTOs, mappers, and repository implementations |
| `di/` | Hilt dependency modules |
| `utils/` | Cart calculations and response handling |

Source root: [app/src/main/java/com/example/milkchequedemo](app/src/main/java/com/example/milkchequedemo).

## Run locally

1. Clone this repository and open it in Android Studio.
2. Install Android SDK 36 and use JDK 17 for the Gradle build.
3. Sync Gradle.
4. Check the backend base URL in [StoreApiProvider.kt](app/src/main/java/com/example/milkchequedemo/data/service/StoreApiProvider.kt). Replace it with a compatible backend if needed; keep the trailing slash.
5. Run the `app` configuration on a device or emulator running Android 7.0 / API 24 or newer.

The configured hosted backend's availability has not been verified. Full menu, ordering, and payment flows require a reachable backend and valid store, table, and session data.

## Backend contract

The client declares the following routes in [StoreApi.kt](app/src/main/java/com/example/milkchequedemo/data/service/StoreApi.kt):

| Method | Route | Purpose |
| --- | --- | --- |
| GET | `store/info` | Store and table information |
| GET | `store/menu` | Menu items |
| POST | `session/add` | Start a session |
| POST | `session/order` | Submit a customer order |
| GET | `session/allOrders` | Retrieve session orders |
| POST | `payments/pay` | Request a payment URL |

Request and response models are in [data/dto](app/src/main/java/com/example/milkchequedemo/data/dto).

## Status

An Android prototype for exploring UI state, layered architecture, API integration, and shared dining workflows. Build and end-to-end behavior have not been verified as part of this documentation update.
