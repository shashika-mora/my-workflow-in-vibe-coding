# Antigravity Mobile Stack (Flutter)

## 1. Core Technologies
*   **Framework:** Flutter (Latest Stable).
*   **Language:** Dart.
    *   *Rule:* **Strict Typing** enabled. No `dynamic` unless absolutely necessary.
*   **Architecture:** Riverpod (Preferred) or Bloc/Cubit.
    *   *Pattern:* unidirectional data flow.

## 2. Component Structure
*   **Screens:** Full page widgets.
    *   `lib/features/chat/presentation/screens/chat_screen.dart`
*   **Widgets:** Reusable UI components.
    *   `lib/core/widgets/app_button.dart`
*   **State Management:** Keep logic out of UI. Use Consumers/BlocBuilders.

## 3. Golden Scaffold
```text
lib/
├── main.dart             # Entry point
├── core/
│   ├── theme/            # AppTheme, Colors
│   ├── utils/            # Constants, formatters
│   └── widgets/          # Shared widgets (Buttons, Inputs)
├── features/
│   ├── auth/
│   │   ├── data/
│   │   ├── domain/
│   │   └── presentation/ # Screens, Widgets, Providers/Blocs
│   └── home/
└── l10n/                 # Localization (arb files)
```

## 4. Dependencies
*   **Routing:** GoRouter (standard for deep linking support).
*   **Network:** Dio (better interceptors than http).
*   **Local Storage:** Hive or Shared Preferences.
*   **Freezed:** Recommended for immutable data classes and unions.

## 5. Vibe Rules
*   **No Spaghettification:** Break `build` methods down. If a widget is > 100 lines, extract sub-widgets.
*   **Const Everything:** Use `const` constructors wherever possible for performance.
