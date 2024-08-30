## Android Emulator Setup Script

**Overview**

This project provides a script to automate the creation and startup of an Android Emulator with API level 33. It is designed to work seamlessly on Linux and macOS-13 runners. Future updates may include support for additional API levels and operating systems.

**Features**

- **Automated Setup:** Quickly create and start an Android Emulator with API 33.
- **Platform Support:** Compatible with Linux and macOS-13 runners.
- **Future-Proof:** Additional API levels and platform support planned for future releases.

**Prerequisites**

- **Operating System:**
  
  - Linux
  - macOS-13
  
- **Java JDK:** Must be installed before running the script.

**Future Updates**
- **API Level Support:** We plan to add support for additional API levels in upcoming releases.
- **Additional Platforms:** Evaluation for support on other operating systems is ongoing.

## Example GitHub Actions Workflow

To integrate the Android Emulator setup into your CI/CD pipeline using GitHub Actions, you can use the following workflow example:

```yaml
# .github/workflows/android-emulator.yml

name: Android Emulator Setup

on:
  push:
    branches:
      - main
  pull_request:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout repository
      uses: actions/checkout@v2

    - name: Set up JDK 22
      uses: actions/setup-java@v3
      with:
        java-version: '22'
        distribution: 'temurin'
      
    - name: Create and start emulator
      uses: ThangNguyen0495/create-android-emulator@v1.0.0
      
    - name: Run tests
      run: mvn test
