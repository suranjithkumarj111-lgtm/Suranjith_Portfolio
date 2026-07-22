# CTV Multi-Platform Automation Framework

## Overview
A comprehensive automation framework for Connected TV (CTV) platforms including Samsung TV (Tizen), LG TV (WebOS), Fire TV, and Android TV. Built for the Disney+ streaming platform at GlobalLogic.

## Problem Statement
Testing streaming applications across multiple CTV platforms required separate tooling, different protocols, and extensive manual validation. There was no unified approach to automate tests across all platforms.

## Solution
Developed a unified automation framework using Appium with JavaScript that abstracts platform-specific complexities and provides a single interface for cross-platform CTV testing.

## Supported Platforms
| Platform | OS | Protocol |
|----------|-----|----------|
| Samsung TV | Tizen | Appium + WebDriver |
| LG TV | WebOS | Appium + WebDriver |
| Amazon Fire TV | Fire OS | Appium + ADB |
| Android TV | Android | Appium + UiAutomator |

## Tech Stack
- **Appium** - Mobile/CTV automation engine
- **JavaScript/Node.js** - Test scripting
- **WebDriverIO** - Test framework
- **Jenkins** - CI/CD pipeline
- **BrowserStack / HeadSpin** - Cloud device farm

## Key Features
- Cross-platform test execution with single codebase
- Remote device control via cloud testing platforms
- Automated smoke, regression, and sanity suites
- Video recording and screenshot capture
- Custom reporting with Allure

## Project Structure
```
ctv-automation-framework/
├── config/
│   ├── samsung.config.js
│   ├── lg.config.js
│   ├── firetv.config.js
│   └── androidtv.config.js
├── tests/
│   ├── smoke/
│   ├── regression/
│   └── sanity/
├── pages/
│   ├── home.page.js
│   ├── player.page.js
│   └── search.page.js
├── utils/
│   ├── remote-control.js
│   └── device-manager.js
└── package.json
```

## How to Run
```bash
npm install
npm run test:samsung
npm run test:lg
npm run test:firetv
npm run test:all
```

## Author
**Suranjith Kumar J** - Senior SDET-2 | AI-Powered QAOps Engineer  
[LinkedIn](https://linkedin.com/in/suranjith-kumar-jeppu) | [Portfolio](https://suranjithkumarj111-lgtm.github.io/Suranjith_Portfolio)
