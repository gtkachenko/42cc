# Project Name

This project uses GitLab CI/CD for continuous integration and deployment.

## CI/CD Stages

### Lint Dockerfile
- Lints the Dockerfile in the specified folder.

### Lint Python
- Lints the Python code using Flake8.

### Lint Ansible
- Lints Ansible code using Ansible Lint and generates a JUnit report.

### Code Coverage
- Measures code coverage using pytest and generates a coverage report.

### Test
- Executes tests using pytest.

### SonarQube Check
- Runs SonarQube analysis and checks for code quality. Requires code coverage from the "Code Coverage" stage.

### Packaging
- Uses Kaniko to build and package the Docker image.

### Update Kubernetes Manifest
- Updates the Kubernetes deployment manifest with the new Docker image tag.

### Deploy
- Deploys the application using Ansible.

## Default CI/CD Settings

- **Runner Tag:** demo-runner
- **Dockerfile Folder:** Docker/calc
- **CI Registry Image:** gtkachenko1990

## How to Use

1. Fork/Clone the repository.

2. Configure CI/CD settings in `.gitlab-ci.yml`:
    - Set your Dockerfile folder in `DOCKER_FILE_FOLDER`.
    - Adjust the `CI_REGISTRY_IMAGE` according to your GitLab Container Registry.

3. Create a pipeline:
    - Push changes to the repository.
    - The pipeline will run linting, testing, code coverage, and deployment stages.

## Branch Strategy

- The `main` branch triggers deployment on successful packaging and testing.
- Merge requests trigger pipeline events to ensure code quality and tests.

## Contributing

Feel free to contribute to improve our CI/CD setup. Follow the [contribution guidelines](CONTRIBUTING.md).

## License

This project is licensed under the [License Name]. See the [LICENSE](LICENSE) file for details.
