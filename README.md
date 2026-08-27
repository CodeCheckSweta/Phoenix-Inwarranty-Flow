# Phoenix In-Warranty API Automation

<p align="center">
  <strong>Postman API Automation + Newman + GitHub Actions CI/CD</strong>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Postman-FF6C37?style=for-the-badge&logo=postman&logoColor=white" />
  <img src="https://img.shields.io/badge/Newman-FF6C37?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Node.js-22-339933?style=for-the-badge&logo=nodedotjs&logoColor=white" />
  <img src="https://img.shields.io/badge/GitHub%20Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white" />
</p>

<p align="center">
  <a href="https://codechecksweta.github.io/Phoenix-Inwarranty-Flow/">📊 View Latest Test Report</a>
</p>

---

## 📌 Overview

**Phoenix In-Warranty Flow** is an API automation POC demonstrating how **Postman collections can be integrated into a CI/CD pipeline using Newman and GitHub Actions**.

The project validates an end-to-end in-warranty workflow using reusable API requests, environment variables, CSV-driven test data, authentication/token validation, negative scenarios, and JSON schema validation.

The automation pipeline can be triggered automatically, manually, or on a schedule. Test reports are generated as HTML artifacts and published through GitHub Pages.

## 🎯 Key Highlights

- 🔌 **Postman collection-based API automation**
- 🚀 **Newman CLI execution**
- 🔄 **GitHub Actions CI/CD integration**
- 📊 **HTML reporting with Newman HTML Extra**
- 📁 **CSV-based data-driven testing**
- 🔐 **Secrets managed through GitHub Secrets**
- 🧩 **JSON schema validation**
- ❌ **Negative and edge-case testing**
- 🔑 **Authentication/token validation**
- 🌐 **GitHub Pages test-report publishing**
- 📧 **Automated email notification after execution**

---

## 🧪 Testing Coverage

| Test Area | Coverage |
| --- | --- |
| **Happy Path** | End-to-end in-warranty workflow validation |
| **Negative Testing** | Invalid inputs and failure scenarios |
| **Edge Cases** | Boundary and unexpected data validation |
| **Authentication** | Token/login validation |
| **Data-Driven Testing** | CSV-based test data execution |
| **Schema Validation** | API response contract validation |
| **Regression Execution** | Automated suite execution through CI/CD |

---

## 🏗️ CI/CD Architecture

```text
                    ┌──────────────────────┐
                    │   GitHub Repository  │
                    └──────────┬───────────┘
                               │
                 Push / Manual / Scheduled
                               │
                               ▼
                    ┌──────────────────────┐
                    │   GitHub Actions     │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │   Node.js 22         │
                    │   Newman             │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │ Postman Collection   │
                    │ + Environment        │
                    │ + CSV Test Data      │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │ API Test Execution   │
                    └───────┬───────┬──────┘
                            │       │
                 ┌──────────┘       └──────────┐
                 ▼                             ▼
        ┌────────────────┐             ┌────────────────┐
        │ HTML Report    │             │ Email          │
        │ GitHub Pages   │             │ Notification   │
        └────────────────┘             └────────────────┘
```

The workflow is configured for push, manual, and scheduled execution and uploads the generated Newman report as an artifact. fileciteturn11file0L2-L5

---

## ⚙️ GitHub Actions Workflow

The pipeline performs the following steps:

1. **Checkout** the repository
2. Set up **Node.js 22**
3. Install **Newman** and **newman-reporter-htmlextra**
4. Execute the Postman collection
5. Generate an HTML report
6. Upload the report as a GitHub Actions artifact
7. Publish the report to **GitHub Pages**
8. Send an email notification

The workflow uses `if: always()` for reporting, publishing, and notification steps so that reporting/notification can still happen when the test execution fails. fileciteturn11file0L2-L2

### Triggering the Pipeline

The workflow supports:

```text
Push to main
      OR
Manual workflow_dispatch
      OR
Scheduled cron execution
```

---

## 📊 Test Report

The latest generated HTML report is published here:

**[View Latest Phoenix In-Warranty Test Report](https://codechecksweta.github.io/Phoenix-Inwarranty-Flow/)**

Reports are also uploaded as GitHub Actions artifacts for later inspection. fileciteturn11file0L2-L2

### Example Report

![Newman HTML Report](https://github.com/CodeCheckSweta/Phoenix-Inwarranty-Flow/blob/static-content/newman-report.png)

---

## 📂 Project Structure

```text
Phoenix-Inwarranty-Flow/
├── Inwarranty-flow Collection.postman_collection.json
├── QA.postman_environment.json
├── testdata.csv
├── newman/
│   └── index.html                 # Generated HTML report
└── .github/
    └── workflows/
        └── main.yml               # GitHub Actions pipeline
```

> The `newman/index.html` report is generated during execution and should not be treated as source test data.

---

## ▶️ Run Locally

### Prerequisites

- Node.js 22+
- npm
- Postman/Newman-compatible collection
- Git

### Clone the repository

```bash
git clone https://github.com/CodeCheckSweta/Phoenix-Inwarranty-Flow.git
cd Phoenix-Inwarranty-Flow
```

### Install Newman

```bash
npm install -g newman
npm install -g newman-reporter-htmlextra
```

### Execute the collection

```bash
newman run "Inwarranty-flow Collection.postman_collection.json" \
  -e QA.postman_environment.json \
  -d testdata.csv \
  -r cli,htmlextra \
  --reporter-htmlextra-export ./newman/index.html
```

### Expected output

```text
CLI results
     ↓
Newman HTML Extra Report
     ↓
./newman/index.html
```

---

## 🔐 Security & Secrets

Sensitive credentials are **not intended to be committed to source control**.

For CI/CD execution, credentials and SMTP configuration are supplied through **GitHub Secrets**. The workflow references secret values for email authentication rather than hard-coding passwords. fileciteturn11file0L2-L2

Recommended secrets include:

```text
EMAIL_USERNAME
EMAIL_PASSWORD
```

If additional API credentials are required, they should also be stored as repository/environment secrets.

---

## 🛠️ Technology Stack

| Tool | Role |
| --- | --- |
| **Postman** | API collection development |
| **Newman** | CLI test execution |
| **newman-reporter-htmlextra** | HTML reporting |
| **Node.js 22** | Runtime |
| **GitHub Actions** | CI/CD automation |
| **GitHub Pages** | Report publishing |
| **CSV** | Data-driven testing |
| **Gmail SMTP** | Execution notifications |

The current workflow installs Node.js 22 and Newman tooling during the GitHub Actions run. fileciteturn11file0L2-L2

---

## 💡 Why This Project Matters

This project demonstrates more than API testing. It shows how a QA engineer can take automated API tests and integrate them into a **continuous quality pipeline**:

```text
API Tests
   ↓
CLI Automation
   ↓
CI/CD
   ↓
Automated Regression
   ↓
Test Reporting
   ↓
Stakeholder Notification
```

This approach enables automated quality feedback without requiring testers to manually start the collection or distribute reports after every execution.

---

## 🚀 Potential Enhancements

- [ ] Add separate QA/UAT/Production environment configurations
- [ ] Add test result summary directly to GitHub Actions
- [ ] Add pass/fail trend tracking
- [ ] Add reusable workflow inputs for environment selection
- [ ] Add API contract testing across environments
- [ ] Add automated issue creation for critical failures
- [ ] Add richer Slack/Teams notifications
- [ ] Containerise Newman execution with Docker

---

## 👩‍💻 Author

**Sweta Singh — Senior QA Engineer / SDET**

10+ years of experience across **test automation, API testing, Selenium, Playwright, CI/CD, Docker, and Quality Engineering**.

[GitHub](https://github.com/CodeCheckSweta) · [LinkedIn](https://www.linkedin.com/in/swetasingh22/)

---

⭐ If you find this project useful, consider starring the repository.
