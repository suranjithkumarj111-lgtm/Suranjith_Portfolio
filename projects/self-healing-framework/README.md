# Self-Healing Test Automation Framework

## Overview
An AI-powered test automation framework with self-healing capabilities that automatically detects UI changes and adapts element locators without manual intervention.

## Problem Statement
UI-based automation tests break frequently due to:
- Dynamic element IDs/attributes
- CSS/layout changes from feature updates
- A/B testing variations
- Minor UI refactoring

This leads to high maintenance costs and unreliable test suites.

## Solution
Implemented an intelligent locator strategy with multiple fallback mechanisms and ML-based element matching that automatically heals broken selectors at runtime.

## Tech Stack
| Technology | Purpose |
|-----------|---------|
| Java | Core framework |
| Selenium WebDriver | Browser automation |
| TestNG | Test execution |
| ML Algorithms | Smart element matching |
| Maven | Build management |

## How Self-Healing Works
```
Test Execution --> Element Not Found?
                        |
                   Yes ──┼── No --> Continue
                        |
              Try Alternative Locators
              (ID, Name, CSS, XPath, Text)
                        |
              ML-Based Visual Matching
                        |
              Element Found? ──── No --> Fail & Log
                        |
                       Yes
                        |
              Update Locator Cache
              Continue Test Execution
              Log Healing Event
```

## Key Features
- **Multi-strategy locator**: Falls back through ID → Name → CSS → XPath → Text
- **Smart XPath generation**: Generates relative XPaths from element attributes
- **Visual matching**: Uses element position, size, and visual properties
- **Healing reports**: Logs all healed elements for review
- **Locator cache**: Stores successful alternatives for future runs

## Configuration
```java
@SelfHealing(
    strategies = {Strategy.ID, Strategy.CSS, Strategy.XPATH, Strategy.VISUAL},
    maxAttempts = 3,
    reportHealing = true
)
public class LoginPage extends BasePage {
    @FindBy(id = "username")
    private WebElement usernameField;
}
```

## Key Results
- 40% reduction in test maintenance effort
- 90%+ auto-recovery rate for broken locators
- Near-zero false failures from UI changes
- Detailed healing reports for developers

## How to Run
```bash
mvn clean test -Dtest.suite=regression
mvn allure:report
```

## Author
**Suranjith Kumar J** - Senior SDET-2 | AI-Powered QAOps Engineer  
[LinkedIn](https://linkedin.com/in/suranjith-kumar-jeppu) | [Portfolio](https://suranjithkumarj111-lgtm.github.io/Suranjith_Portfolio)
