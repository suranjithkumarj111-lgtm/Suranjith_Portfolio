# Jenkins CI/CD Pipeline Automation

## Overview
End-to-end Jenkins pipeline automation for build validation, test execution, reporting, and deployment verification. Supports pre-production validation with automated regression suites.

## Problem Statement
Manual build validation and test execution before releases was slow, error-prone, and lacked consistent feedback loops. Teams often discovered defects late in the release cycle.

## Solution
Built comprehensive Jenkins pipelines with:
- Automated build validation triggers
- Smart test selection based on code changes
- Parallel test execution across environments
- Automated reporting and notifications
- Pre-production deployment verification

## Tech Stack
| Technology | Purpose |
|-----------|---------|
| Jenkins | CI/CD orchestration |
| Pipeline as Code (Groovy) | Pipeline definitions |
| GitHub / GitHub Actions | SCM & webhooks |
| Maven | Build tool |
| Docker | Execution environments |
| Allure | Test reporting |

## Pipeline Stages
```
Code Push --> GitHub Webhook --> Jenkins Trigger
                                      |
                              ┌───────┴───────┐
                              │  Build Stage  │
                              │  Maven Build  │
                              │  Code Quality │
                              └───────┬───────┘
                                      |
                              ┌───────┴───────┐
                              │  Test Stage   │
                              │  Smoke Tests  │
                              │  Regression   │
                              │  Integration  │
                              └───────┬───────┘
                                      |
                              ┌───────┴───────┐
                              │ Report Stage  │
                              │ Allure Report │
                              │ Slack Notify  │
                              └───────┬───────┘
                                      |
                              ┌───────┴───────┐
                              │ Deploy Stage  │
                              │ Pre-Prod BVT  │
                              │ Sanity Check  │
                              └───────────────┘
```

## Jenkinsfile Example
```groovy
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('Test') {
            parallel {
                stage('Smoke') {
                    steps {
                        sh 'mvn test -Dsuite=smoke'
                    }
                }
                stage('Regression') {
                    steps {
                        sh 'mvn test -Dsuite=regression'
                    }
                }
            }
        }

        stage('Report') {
            steps {
                allure includeProperties: false,
                       results: [[path: 'target/allure-results']]
            }
        }

        stage('Deploy Verification') {
            when { branch 'release/*' }
            steps {
                sh 'mvn test -Dsuite=bvt -Denv=preprod'
            }
        }
    }

    post {
        always {
            slackSend channel: '#qa-alerts',
                      message: "Build ${currentBuild.result}: ${env.JOB_NAME}"
        }
    }
}
```

## Key Results
- 50% faster release cycles
- Early defect detection (shift-left)
- Automated pre-production validation
- Real-time Slack notifications
- Complete audit trail of all test runs

## How to Run
```bash
jenkins-cli build 'Automation/smoke-test' -p ENV=qa
jenkins-cli build 'Automation/regression' -p ENV=staging
```

## Author
**Suranjith Kumar J** - Senior SDET-2 | AI-Powered QAOps Engineer  
[LinkedIn](https://linkedin.com/in/suranjith-kumar-jeppu) | [Portfolio](https://suranjithkumarj111-lgtm.github.io/Suranjith_Projects)
