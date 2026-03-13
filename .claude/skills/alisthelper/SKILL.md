# alisthelper Development Patterns

> Auto-generated skill from repository analysis

## Overview

This skill teaches development patterns for alisthelper, a Swift-based application that manages AList and Rclone services. The codebase follows conventional commit patterns, uses snake_case file naming, and emphasizes state management through Riverpod providers with comprehensive internationalization support.

## Coding Conventions

### File Naming
- Use `snake_case` for all file names
- Examples: `alist_provider.dart`, `rclone_state.dart`, `main_page.dart`

### Import Style
```swift
// Mixed import style - organize by type
import 'dart:io';
import 'package:flutter/material.dart';
import 'package:riverpod/riverpod.dart';

import '../model/alist_state.dart';
import '../provider/alist_provider.dart';
```

### Commit Messages
Follow conventional commit format with these prefixes:
- `feat:` - New features
- `fix:` - Bug fixes
- `docs:` - Documentation updates
- `chore:` - Maintenance tasks
- `perf:` - Performance improvements
- `build:` - Build system changes
- `style:` - Code style changes

Average commit message length: 42 characters

## Workflows

### Dependency Update
**Trigger:** When maintaining dependencies or fixing security vulnerabilities
**Command:** `/update-deps`

1. Update `pubspec.yaml` with new dependency versions
2. Run `flutter pub get` to resolve dependencies
3. Update `pubspec.lock` with resolved versions
4. Test application functionality
5. Commit with message: `chore: update dependencies to latest versions`

### CI Workflow Update
**Trigger:** When improving build process or updating action versions
**Command:** `/update-ci`

1. Update GitHub Action versions in `.github/workflows/main.yml`
2. Modify workflow configuration in `.github/workflows/nightly.yml`
3. Add new build steps or permissions as needed
4. Test workflow changes
5. Commit with message: `build: update CI workflows and actions`

### State Management Refactor
**Trigger:** When improving state management architecture or converting to new patterns
**Command:** `/refactor-state`

1. Update state model classes in `lib/model/*_state.dart`
2. Refactor provider implementations in `lib/provider/*_provider.dart`
3. Update widget consumers in `lib/widgets/*.dart`
4. Ensure proper state isolation and immutability
5. Test state transitions and UI updates
6. Commit with message: `refactor: improve state management patterns`

Example state class pattern:
```dart
class AlistState {
  final bool isRunning;
  final String status;
  final List<String> logs;
  
  const AlistState({
    required this.isRunning,
    required this.status,
    required this.logs,
  });
  
  AlistState copyWith({
    bool? isRunning,
    String? status,
    List<String>? logs,
  }) {
    return AlistState(
      isRunning: isRunning ?? this.isRunning,
      status: status ?? this.status,
      logs: logs ?? this.logs,
    );
  }
}
```

### Localization Update
**Trigger:** When adding new UI text or updating translations
**Command:** `/update-i18n`

1. Update base language file `lib/i18n/en.i18n.json`
2. Update Chinese Simplified `lib/i18n/zh-Hans-CN.i18n.json`
3. Update Chinese Traditional `lib/i18n/zh-Hant-TW.i18n.json`
4. Add new translation keys consistently across all files
5. Verify translations in UI
6. Commit with message: `feat: update localization strings`

Example i18n structure:
```json
{
  "common": {
    "start": "Start",
    "stop": "Stop",
    "settings": "Settings"
  },
  "alist": {
    "status": "AList Status",
    "running": "Running",
    "stopped": "Stopped"
  }
}
```

### Provider Enhancement
**Trigger:** When adding new features to AList or Rclone management
**Command:** `/enhance-provider`

1. Update provider logic in `lib/provider/alist_provider.dart` or `lib/provider/rclone_provider.dart`
2. Add new state fields to corresponding state models
3. Update related UI components to use new functionality
4. Ensure proper error handling and state updates
5. Test provider functionality thoroughly
6. Commit with message: `feat: enhance [provider] with new functionality`

### UI Widget Refactor
**Trigger:** When standardizing UI components or improving user experience
**Command:** `/refactor-ui`

1. Update widget implementations in `lib/widgets/pages/*.dart`
2. Standardize button styles and common components
3. Improve layout patterns and responsive design
4. Ensure consistent theming across widgets
5. Test UI changes on different screen sizes
6. Commit with message: `style: refactor UI widgets for consistency`

## Testing Patterns

Tests follow the `*.test.*` naming pattern. While the specific testing framework wasn't detected, ensure:
- Unit tests for state management logic
- Widget tests for UI components
- Integration tests for provider interactions
- Mock external dependencies appropriately

## Commands

| Command | Purpose |
|---------|---------|
| `/update-deps` | Update project dependencies to latest versions |
| `/update-ci` | Update GitHub Actions workflows and CI configuration |
| `/refactor-state` | Refactor state management patterns using Riverpod |
| `/update-i18n` | Update internationalization files and translations |
| `/enhance-provider` | Enhance AList or Rclone providers with new features |
| `/refactor-ui` | Refactor UI widgets for consistency and better UX |