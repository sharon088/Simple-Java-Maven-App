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


## GitHub Actions CI/CD
This project includes a GitHub Actions workflow for continuous integration and deployment. The workflow is defined in .github/workflows/java-ci.yml. It automates the following tasks:

1. Increment version: The version in pom.xml is incremented automatically with each push to the master branch.

2. Docker Build & Push: After building the application, the Docker image is pushed to Docker Hub.

3. Run Docker container: The workflow runs the built Docker container to ensure the application works correctly.


## GitHub Actions Key points:
- Versioning: The version in pom.xml is automatically incremented on every push to master.
- Docker Hub Integration: The Docker image is tagged with the version number and pushed to Docker Hub for distribution.
- Build Caching: Maven dependencies are cached for faster builds using GitHub Actions cache.

## Dockerfile:
The Dockerfile is set up for a multi-stage build to keep the runtime image small and efficient. It first builds the project with Maven and then creates a runtime image based on OpenJDK 17.

   ```bash
   # Stage 1: Build the application
   FROM maven:3.9.9-eclipse-temurin-21-alpine AS build
   WORKDIR /app
   COPY . .
   RUN mvn clean verify

   # Stage 2: Create the runtime image
   FROM openjdk:17-jdk-slim
   WORKDIR /app
   COPY --from=build /app/target/my-app-*.jar app.jar
   EXPOSE 8080
   CMD ["java", "-jar", "app.jar"]
   ```
