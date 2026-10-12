# CI/CD Quality Pipeline

## Project Overview

This project demonstrates a beginner-friendly Continuous Integration and Continuous Delivery (CI/CD) quality pipeline using JavaScript, Jest, npm, and GitHub Actions.

The pipeline automatically installs project dependencies and runs automated tests whenever code is pushed to the repository or a pull request is created or updated.

## Technologies Used

- JavaScript
- Node.js
- npm
- Jest
- Git and GitHub
- GitHub Actions
- YAML

## Automated Tests

The Jest test suite contains three automated checks:

| Test | Purpose |
|---|---|
| Application Status | Checks that the application status is `OK`. |
| Required Application Data | Checks that an application name exists. |
| Application Version | Checks that the application version matches the expected version. |

## CI/CD Workflow

The GitHub Actions workflow performs these steps:

1. Checks out the repository.
2. Sets up Node.js.
3. Installs dependencies.
4. Runs the Jest test suite.
5. Reports whether the quality checks passed or failed.

The workflow runs automatically on pushes and pull requests.

## Run Locally

Install the dependencies:

```bash
npm install
```

Run the automated tests:

```bash
npm test
```

## What I Learned

- Writing automated tests with Jest.
- Managing JavaScript dependencies with npm.
- Creating a GitHub Actions workflow.
- Automating quality checks on code changes.
- Using test results to identify problems in a CI pipeline.

## Project Status

The GitHub Actions workflow is passing, and all three Jest tests pass locally.


