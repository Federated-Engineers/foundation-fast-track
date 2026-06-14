## Challenge

You must create a local codebase that intentionally challenges an automated pipeline's linting and formatting rules. 
Once the pipeline enforces clean standards, it must autonomously build your application into a Docker container image 
and securely ship it to your remote public container registry (Dockerhub).

### 1. The Application Component

- Create a simple Python script that reads from an API and save the data after some transformation as a parquet file.

### 2. The Packaging Component

- Write a Dockerfile file to containerize your Python application.

### 3. The Continuous Integration (CI) 

- Implement a GitHub Actions workflow that triggers dynamically on any code push or pull request to your branch.

- Integrate two explicit quality tools: `flake8` (to assert style and syntax compliance) and `isort` (to assert that import hierarchies are organized cleanly).

- The pipeline must be designed to throw an immediate error code and stop running if either of these tools detects structural messiness.

### 4. The Continuous Delivery (CD)

- Establish a separate deployment sequence within the same workflow.

- Hard Rule: This deployment sequence must possess an explicit dependency tag. It must never run if the code quality verification step fails or is skipped.

- Use secure environment parameters to handle authentication. Your clear-text passwords or secret credentials must never be hardcoded directly into the workflow file.

- Upon successful authentication, the workflow must compile the container and push it to your remote registry with a tracking tag.

Good Luck!!!
