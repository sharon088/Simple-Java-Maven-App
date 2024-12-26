# Java Maven Project with Docker and GitHub Actions

This project demonstrates a Maven-based Java application with Docker integration and CI/CD using GitHub Actions. It covers the following best practices:

- Multi-stage Docker builds for optimized images.
- Automatic version increment on every push.
- Maven project setup with Java 17 and JUnit 5.
- Docker image build and push to Docker Hub.
- CI/CD pipeline using GitHub Actions.



## Prerequisites

Ensure you have the following tools installed:

- **Maven**: A build automation tool for Java projects.
- **Docker**: A containerization platform to build and run Docker images.
- **GitHub Account**: For storing and managing the repository.
- **Docker Hub Account**: For pushing Docker images.

## Setup and Build

1. **Clone the repository**:

   ```bash
   git clone https://github.com/yourusername/my-app.git
   cd my-app
   ```

2. **Build the project locally using Maven:**:

   ```bash
   mvn clean verify
   ```

3. **Build and run the Docker image:**:
  - First, build the Docker image:
   ```bash
   docker build -t my-app .
   ```
  - Run the Docker container:
   ```bash
   docker run --rm my-app
   ```


