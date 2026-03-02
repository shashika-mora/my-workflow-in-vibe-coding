---
trigger: always_on
---

# Antigravity Mobile Stack

## 1. Platform Selection Strategy
*   **Native Android (Primary):** Use **Kotlin** and Android Studio for platform-specific experiences, heavy OS integration (Bluetooth, Sensors, Widgets), or peak performance.
*   **Cross-Platform (Secondary):** Use **Flutter (Dart)** only when the user explicitly requests a cross-platform solution (iOS + Android) and the app does not rely heavily on native-specific hardware APIs.

---

## 2. Native Android (Kotlin) Guidelines
*   **Paradigm:** Treat Kotlin exactly like modern Java. Strictly adhere to Object-Oriented Programming (OOP) concepts, SOLID principles, and clean architecture.
*   **UI Framework:** **Jetpack Compose** is mandatory. Do not use legacy XML layouts unless maintaining old code.
    *   *Rule:* Keep Composable functions pure. Pass state down and hoist events up.
*   **Architecture:** **MVVM (Model-View-ViewModel)** is the standard.
    *   *Model:* Repositories and Data Sources (Room, Retrofit).
    *   *ViewModel:* Holds UI state (StateFlow/LiveData) and business logic. No `android.*` imports allowed here.
    *   *View:* Jetpack Compose UI reacting to ViewModel state.
*   **Asynchrony:** Use **Kotlin Coroutines** and `Flow` for all background threading.
*   **Dependency Injection:** Use **Hilt** or **Dagger** to enforce Dependency Inversion and aid in testing.

---

## 3. Cross-Platform (Flutter) Guidelines
*   **Language:** Dart with strict typing enabled. Absolutely no `dynamic` types.
*   **Architecture:** **Riverpod** is the preferred state management solution. Maintain strict separation of concerns (UI vs Logic).
*   **Widget Rules:** 
    *   Extract large `build` methods into separate Widget classes.
    *   Use `const` constructors aggressively on all static widgets to prevent unnecessary rebuilds.

---

## 4. Mobile Optimizations & Performance
*   **Memory Management:** 
    *   Avoid object churning within `onDraw` (Android) or `build` (Flutter) methods.
    *   Properly cancel Coroutines/Streams when ViewModels or Widgets are disposed to prevent memory leaks.
*   **Image Caching:** Always use established caching libraries (e.g., Coil for Android, `cached_network_image` for Flutter) rather than fetching images repeatedly over the network.
*   **List Views:** Always use lazy loading mechanisms (`LazyColumn` in Compose, `ListView.builder` in Flutter) for long lists to recycle views/widgets.

---

## 5. Non-Functional Requirements (NFRs)
Every mobile application must be built with the following NFRs guaranteed:
*   **Offline First:** The app should handle network unavailability gracefully. Cache critical data locally using **Room** (Android) or **Hive/Isar** (Flutter).
*   **Security:** 
    *   Never log sensitive user data.
    *   Use **EncryptedSharedPreferences** (Android) or **flutter_secure_storage** (Flutter) for auth tokens.
    *   Enforce certificate pinning for critical API requests.
*   **Battery & Network Efficiency:** Batch network requests. Avoid aggressive unmetered polling; rely on Push Notifications (FCM) or WorkManager for background syncs.
*   **Accessibility:** Ensure minimum contrast ratios, support dynamic font scaling, and provide content descriptions (`Modifier.semantics` in Compose, `Semantics` widget in Flutter) for visually impaired users.
