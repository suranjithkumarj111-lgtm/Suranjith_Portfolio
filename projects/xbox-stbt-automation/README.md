# Xbox STBT Automation (Disney+)

## Overview
Python-based test automation for Xbox console testing using the STBT (Stb-tester) framework. Automates visual-based testing for the Disney+ streaming application on gaming consoles.

## Problem Statement
Xbox gaming console testing for streaming applications required visual validation approaches since traditional DOM-based automation isn't possible on console platforms.

## Solution
Utilized STBT (Set-top Box Tester) framework with Python to implement image-recognition-based testing that validates UI elements, video playback, and navigation flows on Xbox hardware.

## Tech Stack
| Technology | Purpose |
|-----------|---------|
| Python | Test scripting |
| STBT Framework | Visual test automation |
| Xbox DevKit | Console hardware |
| OpenCV | Image processing |
| Jenkins | CI/CD integration |

## Key Features
- Image-based element detection and validation
- Video playback quality verification
- Navigation flow automation via remote control simulation
- Screenshot comparison for regression detection
- Automated test reporting with visual evidence

## Test Example
```python
import stbt

def test_disney_plus_launch():
    """Verify Disney+ app launches successfully on Xbox"""
    stbt.press("xbox_button")
    stbt.wait_for_match("images/disney_plus_icon.png", timeout_secs=10)
    stbt.press("a_button")
    assert stbt.wait_for_match("images/home_screen.png", timeout_secs=15)

def test_video_playback():
    """Verify video plays without buffering"""
    navigate_to_content()
    stbt.press("a_button")
    assert stbt.wait_for_motion(timeout_secs=10)
    assert not stbt.detect_match("images/buffering_spinner.png")
```

## Key Results
- Console-grade visual testing automation
- Reduced manual QA effort for Xbox platform
- Integrated into CI/CD for release validation
- Visual regression detection across builds

## How to Run
```bash
stbt run tests/test_launch.py
stbt run tests/test_playback.py
stbt batch run tests/
```

## Author
**Suranjith Kumar J** - Senior SDET-2 | AI-Powered QAOps Engineer  
[LinkedIn](https://linkedin.com/in/suranjith-kumar-jeppu) | [Portfolio](https://suranjithkumarj111-lgtm.github.io/Suranjith_Projects)
