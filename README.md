# Expo Go Incompatibility with Third-Party Libraries Accessing Native Modules

This repository demonstrates an uncommon bug encountered when developing React Native applications using Expo Go and third-party libraries that rely on native modules.  Expo Go's sandboxed environment restricts access to certain native functionalities, leading to errors that are not apparent during development with a physical device or emulator.

## Problem Description

The issue arises when a third-party library attempts to utilize native device capabilities (e.g., camera access, Bluetooth communication) that are not permitted within Expo Go's constraints.  This results in runtime errors specific to the Expo Go environment.

## Solution

The primary solution is to avoid using libraries with heavy reliance on native modules when testing within Expo Go.  Alternative approaches include:

1. **Testing on a physical device or emulator:** This bypasses the Expo Go limitations and provides a more accurate reflection of the app's behavior in a production environment.
2. **Using Expo's managed workflow with EAS Build:**  This approach allows building a standalone app that can access native modules without the restrictions of Expo Go.
3. **Conditional logic:** Implement conditional logic in your code to handle cases where native modules are unavailable (e.g., fallback to a placeholder component if Camera is unavailable in Expo Go).

## Reproduction

1. Clone this repository.
2. Navigate to the project directory and run `npm install`.
3. Attempt to run the application using Expo Go. Observe the error related to the attempted access of native modules.
4. Run the application on a physical device or emulator; it should function correctly.

## Code Samples

The repository contains two JavaScript files:

- `bug.js`: Demonstrates the code that triggers the error in Expo Go.
- `bugSolution.js`: Presents solutions to mitigate the issue using conditional logic and alternative testing environments.