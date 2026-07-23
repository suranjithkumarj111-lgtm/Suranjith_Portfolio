# AI-Driven Subtitle Verification Engine

## Overview
An AI-powered automation system for verifying subtitle accuracy, timing, and synchronization across streaming platforms. This POC resolved critical blockers in the automation testing pipeline and accelerated project delivery at GlobalLogic (Discovery Plus D+ Team).

## Problem Statement
Manual subtitle verification across multiple streaming platforms was time-consuming, error-prone, and couldn't scale with the volume of content being released.

## Solution
Built an AI-driven verification engine that automates:
- Subtitle text accuracy validation using NLP
- Timing/synchronization verification
- Language compliance checking
- Format and positioning validation

## Tech Stack
| Technology | Purpose |
|-----------|---------|
| Python | Core automation logic |
| AI/ML Models | Intelligent text analysis |
| OCR (Tesseract) | Screen text extraction |
| Selenium | Browser-based content playback |
| Jenkins | CI/CD integration |

## Key Results
- Resolved critical blockers in the automation testing pipeline
- Accelerated project delivery timeline
- Successfully integrated AI validation tools into the QA workflow
- Reduced manual verification effort significantly

## Architecture
```
Content Stream --> Frame Capture --> OCR Extraction --> AI Analysis --> Report Generation
                                                           |
                                                    NLP Validation
                                                    Timing Check
                                                    Format Check
```

## How to Run
```bash
pip install -r requirements.txt
python run_verification.py --config config.yaml
```

## Author
**Suranjith Kumar J** - Senior SDET-2 | AI-Powered QAOps Engineer  
[LinkedIn](https://linkedin.com/in/suranjith-kumar-jeppu) | [Portfolio](https://suranjithkumarj111-lgtm.github.io/Suranjith_Portfolio)
