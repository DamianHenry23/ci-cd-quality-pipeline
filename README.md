# CI/CD Quality Pipeline

## 1. Project Overview

This project demonstrates a basic Continuous Integration (CI) pipeline using JavaScript, Jest, npm, and GitHub Actions.

The workflow automatically installs project dependencies and runs automated tests when code is pushed or a pull request is created or updated. Its purpose is to demonstrate how automated quality checks can help identify problems early in the software development process.

## 2. Technologies Used

- **JavaScript and Node.js** — test implementation and execution
- **Jest** — automated testing framework
- **npm** — dependency management and test scripts
- **Git and GitHub** — version control and source code hosting
- **GitHub Actions** — automated CI workflow
- **YAML** — workflow configuration

## 3. Project Structure

```text
ci-cd-quality-pipeline/
├── .github/
│   └── workflows/
│       └── quality-check.yml
├── tests/
│   ├── quality-check.js
│   └── quality-check.test.js
├── .gitignore
├── package.json
├── package-lock.json
└── README.md
```

**Key files:**

- `quality-check.yml` — defines the GitHub Actions workflow.
- `quality-check.test.js` — contains the Jest test suite.
- `quality-check.js` — contains the original custom quality-check script.
- `package.json` — defines dependencies and npm scripts.
- `package-lock.json` — records resolved dependency versions.

## 4. Automated Test Coverage

The Jest suite contains three tests:

| Test | Validation |
|---|---|
| Application Status | Confirms the status is `OK`. |
| Required Application Data | Checks that an application name exists. |
| Application Version | Confirms the version matches the expected value. |

**Latest local test results:**

- Test suites passed: 1
- Tests passed: 3
- Tests failed: 0

These tests validate basic sample values and demonstrate Jest assertions; they do not represent comprehensive testing of a production application.

## 5. CI Workflow

The GitHub Actions workflow runs on pushes and pull requests.

It performs the following steps:

1. Checks out the repository.
2. Sets up Node.js.
3. Installs dependencies using `npm install`.
4. Executes the Jest suite using `npm test`.
5. Reports success or failure.

The pipeline was tested and successfully completed in GitHub Actions.

**Dependency note:** `npm ci` initially failed because of a lock-file synchronization problem. The workflow was changed to use `npm install` as a workaround. Restoring `npm ci` after resolving the lock-file issue would improve installation reproducibility.

## 6. Run Locally

**Prerequisites:** Node.js, npm, and Git.

Clone the repository:

```bash
git clone https://github.com/DamianHenry23/ci-cd-quality-pipeline.git
cd ci-cd-quality-pipeline
```

Install dependencies and run the tests:

```bash
npm install
npm test
```

Jest displays the test results in the terminal.

## 7. Skills Demonstrated

- Writing automated tests with Jest
- Using assertions and organizing test suites
- Managing dependencies with npm
- Configuring GitHub Actions using YAML
- Automating quality checks on code changes
- Investigating CI failures using workflow logs
- Managing source code with Git and GitHub

## 8. Limitations and Future Improvements

This project focuses on basic CI automation. Its tests use hard-coded values, and the pipeline does not yet include linting, coverage thresholds, security scanning, or deployment.

Potential improvements include resolving the lock-file issue to restore `npm ci`, adding negative tests, introducing code coverage reporting, and integrating API or end-to-end tests.

## 9. Project Links

- **Repository:** https://github.com/DamianHenry23/ci-cd-quality-pipeline
- **GitHub Actions:** https://github.com/DamianHenry23/ci-cd-quality-pipeline/actions

## 10. Conclusion

This project provided practical experience integrating automated tests into a CI pipeline, managing dependencies, diagnosing workflow failures, and documenting software quality checks. It establishes a foundation for more advanced Quality Engineering projects.


