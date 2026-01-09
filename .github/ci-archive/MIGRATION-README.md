# Jenkins to GitHub Actions Migration

This document records the migration of Jenkins pipelines in this repository to GitHub Actions.

## Workflows Created
- **Android Build (Flavor from Branch)** — `.github/workflows/android-build.yml`
  - Derives flavor from branch name pattern `QA_<flavor>`; runs Gradle assemble and Crashlytics upload; uploads APK artifacts.
- **SonarQube Gradle Analysis** — `.github/workflows/sonarqube-gradle.yml`
  - Runs `./gradlew clean sonarqube` with SonarQube connection details supplied via secrets.
- **MSBuild** — `.github/workflows/msbuild.yml`
  - Restores NuGet packages and builds the solution on `windows-latest`; publishes `ProjectName/bin/Release/**` artifacts.
- **Node.js Build Test Deploy (Docker)** — `.github/workflows/nodejs-docker.yml`
  - Installs dependencies, runs tests, builds and pushes Docker image, deploys via SSH, then cleans node_modules.
- **Standard Build (Go)** — `.github/workflows/standard-build.yml`
  - Runs inside `golang:1.5` container to build and run `hello-world.go`.

## Required Secrets / Variables
- `SONAR_HOST_URL`, `SONAR_TOKEN` — SonarQube connectivity for Gradle analysis.
- `DOCKER_USERNAME`, `DOCKER_PASSWORD` — Docker registry authentication for image push.
- `DEPLOY_HOST`, `DEPLOY_USER`, `SSH_PRIVATE_KEY` — SSH deployment target and key for Docker deploy step.
- (Optional) Gradle/Crashlytics credentials should be provided via repository secrets or Gradle config as needed by the Android tasks.

## Validation
Action lint executed after migration:
```
$ ./actionlint
(no issues)
```
Actionlint version: 1.7.10

## Archive of Original Jenkins Pipelines
Original Jenkins pipeline definitions have been moved to `.github/ci-archive/`:
- `jenkinsfile-examples/android-build-flavor-from-branch/JenkinsFile`
- `jenkinsfile-examples/sonarqube/Jenkinsfile`
- `jenkinsfile-examples/msbuild/Jenkinsfile`
- `jenkinsfile-examples/nodejs-build-test-deploy-docker-notify/Jenkinsfile`
- `global-library-examples/global-function/Jenkinsfile`
- `global-library-examples/global-function/standardBuild.groovy`

Migration complete. MIGRATION-README.md created in .github/ci-archive/
