# Project CI/CD Configuration

This repository contains the GitLab CI/CD configuration to automate various stages of the development workflow.

## Stages

- **Code Check:** Linting, TypeScript checks, and code formatting checks.
- **Coverage:** Collecting code coverage metrics.
- **Test:** Running unit tests.
- **Package:** Packaging the application.
- **E2E Test:** End-to-end testing.
- **Deploy:** Deployment tasks.
- **Notification:** Sending notifications.

## Jobs

### `check-lint`

- **Description:** Run linting checks.
- **Stage:** Code Check.

### `check-ts`

- **Description:** Run TypeScript checks.
- **Stage:** Code Check.

### `check-format`

- **Description:** Check code formatting.
- **Stage:** Code Checking.

### `code-coverage`

- **Description:** Collect code coverage metrics.
- **Stage:** Coverage.
- **Artifacts:**
  - `${CI_PROJECT_DIR}/backend/coverage/lcov.info`
  - `${CI_PROJECT_DIR}/frontend/coverage/lcov.info`
  - `${CI_PROJECT_DIR}/common/coverage/lcov.info`

### `test`

- **Description:** Run unit tests.
- **Stage:** Test.

### `sonarqube-check`

- **Description:** Run SonarQube checks.
- **Stage:** Test.

### `packaging`

- **Description:** Build and package the application.
- **Stage:** Package.
- **Artifacts:** `frontend/dist/`.

### `e2e-test`

- **Description:** Run end-to-end tests.
- **Stage:** E2E Test.
- **Artifacts:** `${CI_PROJECT_DIR}/e2e/results.json`.

### `deploy`

- **Description:** Deployment tasks.
- **Stage:** Deploy.

### `notification`

- **Description:** Send deployment notification.
- **Stage:** Notification.
- **Needs:** `deploy` job artifacts.

## Pipeline Rules

- For the `code-coverage` job, always run on the `main` branch and merge request events.

- For the `sonarqube-check` job, run only on the default branch and merge request events.

- For the `packaging` job, run on the `main` branch and any release branches matching the pattern.

- For the `notification` job, run only on the `main` branch and only on successful deployments.

## Contributing

Feel free to contribute to improve our CI/CD setup. Follow the [contribution guidelines](CONTRIBUTING.md).

## License

This project is licensed under the [License Name]. See the [LICENSE](LICENSE) file for details.
