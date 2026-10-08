# CI/CD Quality Pipeline

A beginner-friendly Quality Engineering project demonstrating how automated quality checks can be integrated into a Continuous Integration and Continuous Delivery (CI/CD) workflow using GitHub Actions.

The project uses Node.js and GitHub Actions to automatically run quality checks whenever code is pushed to the repository.

---

## Project Overview

The purpose of this project is to demonstrate a basic CI/CD quality pipeline and how automated testing can provide immediate feedback when a change introduces a problem.

The pipeline:

1. Receives a code change through Git.
2. Automatically starts a GitHub Actions workflow.
3. Sets up the Node.js environment.
4. Installs project dependencies.
5. Runs automated quality checks.
6. Reports whether the checks passed or failed.

This project also demonstrates the complete CI/CD feedback cycle:

```text
Code Change
     ↓
Git Push
     ↓
GitHub Actions
     ↓
Automated Quality Checks
     ↓
     ├── PASS → Continue
     │
     └── FAIL → Fix → Push Again
```

---

## Technologies Used

* Node.js
* JavaScript
* Git
* GitHub
* GitHub Actions
* npm
* YAML

---

## Project Structure

```text
ci-cd-quality-pipeline/
│
├── .github/
│   └── workflows/
│       └── quality-check.yml
│
├── tests/
│   └── quality-check.js
│
├── .gitignore
├── package.json
├── package-lock.json
└── README.md
```

---

## Automated Quality Checks

The project currently contains three automated quality checks.

### Check 1 — Application Status

Verifies that the application status matches the expected status.

```javascript
applicationStatus === expectedStatus
```

Expected result:

```text
Application status is OK
```

---

### Check 2 — Required Application Data

Verifies that the application has a required application name.

Expected result:

```text
Application name exists
```

---

### Check 3 — Application Version

Verifies that the application's current version matches the expected version.

Expected result:

```text
Application version is correct
```

---

## Running the Quality Checks Locally

Make sure Node.js is installed.

From the project directory, run:

```bash
node tests/quality-check.js
```

A successful run produces:

```text
Starting Quality Checks...
CHECK 1 PASSED: Application status is OK
CHECK 2 PASSED: Application name exists
CHECK 3 PASSED: Application version is correct
ALL QUALITY CHECKS PASSED
```

If a check fails, the script returns a failure exit code:

```javascript
process.exit(1);
```

If all checks pass, the script returns:

```javascript
process.exit(0);
```

These exit codes allow GitHub Actions to determine whether the workflow should pass or fail.

---

## GitHub Actions Workflow

The CI/CD workflow is located at:

```text
.github/workflows/quality-check.yml
```

The workflow runs automatically whenever code is pushed to GitHub.

The pipeline performs the following steps:

```text
Checkout Repository
        ↓
Set Up Node.js
        ↓
Install Dependencies
        ↓
Run Quality Tests
```

The workflow uses:

```yaml
npm ci
```

to install the dependencies defined in `package-lock.json`.

npm caching is also enabled to improve dependency installation performance during workflow runs.

---

## CI/CD Failure Testing

The pipeline was intentionally tested with failures to verify that it could correctly detect problems.

### Application Status Failure

The application status was intentionally changed from:

```javascript
"OK"
```

to:

```javascript
"ERROR"
```

The local quality check failed as expected.

The change was then pushed to GitHub, where GitHub Actions also reported a failed workflow.

The code was corrected and pushed again, resulting in a successful workflow.

---

### Application Version Failure

The application version was intentionally changed from:

```javascript
"1.0"
```

to:

```javascript
"2.0"
```

while the expected version remained:

```javascript
"1.0"
```

The quality check correctly detected the mismatch.

GitHub Actions also reported the failure.

After correcting the version back to `1.0`, the workflow successfully passed again.

This demonstrated the complete:

```text
Failure
   ↓
Investigation
   ↓
Fix
   ↓
Local Verification
   ↓
Git Push
   ↓
Automated CI Verification
   ↓
Success
```

---

## GitHub Actions Test History

The pipeline has been tested through multiple GitHub Actions workflow runs.

| Run              | Purpose                                | Result   |
| ---------------- | -------------------------------------- | -------- |
| Quality Check #1 | Initial CI/CD pipeline                 | ✅ Passed |
| Quality Check #2 | Intentional application status failure | ❌ Failed |
| Quality Check #3 | Fix application status                 | ✅ Passed |
| Quality Check #4 | Added second quality check             | ✅ Passed |
| Quality Check #5 | Added application version check        | ✅ Passed |
| Quality Check #6 | Intentional version validation failure | ❌ Failed |
| Quality Check #7 | Fixed version validation               | ✅ Passed |
| Quality Check #8 | Improved CI dependency installation    | ✅ Passed |

These runs demonstrate that the pipeline can detect both successful and unsuccessful code changes.

---

## What I Learned

Through this project, I practiced:

* Creating a GitHub Actions workflow
* Running automated checks through CI/CD
* Using Git and GitHub for version control
* Understanding CI/CD feedback cycles
* Using exit codes to communicate test results
* Detecting intentional failures
* Investigating and fixing failed checks
* Verifying fixes locally before pushing
* Using `npm ci` in a CI environment
* Using npm dependency caching in GitHub Actions
* Understanding how automated quality checks can support Quality Engineering

---

## Future Improvements

Possible future improvements could include:

* Adding more meaningful automated tests
* Adding API testing
* Adding test reporting
* Adding linting
* Adding code coverage
* Running tests against multiple Node.js versions
* Adding deployment after successful quality checks

These features are intentionally outside the current beginner scope of the project.

---

## Project Goal

The goal of this project is to demonstrate a practical understanding of how software quality checks can be integrated into a CI/CD pipeline.

It is designed as a small Quality Engineering portfolio project rather than a production CI/CD system.

---

## Author

**Damian Henry**

GitHub:

https://github.com/DamianHenry23
