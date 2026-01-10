# Jenkins Pipeline Examples

> **⚠️ MIGRATION NOTICE:** This repository has been migrated from Jenkins to GitHub Actions!
> 
> - 🎉 **10 GitHub Actions workflows** are now available in `.github/workflows/`
> - 📦 **Original Jenkins files** have been archived in `.github/ci-archive/`
> - 📖 **[Read the full migration guide](.github/ci-archive/MIGRATION-README.md)**

## Introduction

This repository is a home for snippets, tips and tricks and examples of scripting for Jenkins pipelines, now migrated to GitHub Actions workflows.

## GitHub Actions Workflows

The following workflows demonstrate common CI/CD patterns:

| Workflow | Description | Source |
|----------|-------------|--------|
| [Node.js Build & Deploy](/.github/workflows/nodejs-build-test-deploy.yml) | Multi-stage build, test, Docker, deployment, notifications | Jenkins Jenkinsfile |
| [MSBuild .NET](/.github/workflows/msbuild-dotnet.yml) | Windows .NET build with NuGet | Jenkins Jenkinsfile |
| [SonarQube Analysis](/.github/workflows/sonarqube-analysis.yml) | Code quality analysis with Gradle | Jenkins Jenkinsfile |
| [Parallel Execution](/.github/workflows/parallel-execution.yml) | Matrix strategy for parallel jobs | Scripted pipeline |
| [Post Conditions](/.github/workflows/declarative-post-conditions.yml) | Success/failure/always conditions | Declarative pipeline |
| [Credentials & Secrets](/.github/workflows/credentials-secrets.yml) | Using secrets securely | Declarative pipeline |
| [Maven & JDK](/.github/workflows/maven-jdk-version.yml) | Maven build with specific JDK versions | Scripted pipeline |
| [Docker Build](/.github/workflows/docker-build.yml) | Building and running Docker containers | Declarative pipeline |
| [Global Library Example](/.github/workflows/global-library-example.yml) | Shared library expansion | Global library |
| [Reusable Workflow](/.github/workflows/reusable-go-build.yml) | Reusable workflow pattern | Shared library equivalent |

### Quick Start

1. **View Workflows**: Browse `.github/workflows/` for GitHub Actions workflows
2. **Configure Secrets**: Set up required secrets in repository settings
3. **Run Workflows**: Trigger workflows via push, PR, or manual dispatch
4. **View Results**: Check the Actions tab for workflow runs

### Required Secrets

Configure these in **Settings > Secrets and variables > Actions**:

```
DOCKER_USERNAME, DOCKER_PASSWORD    # Docker registry
MAIL_USERNAME, MAIL_PASSWORD        # Email notifications  
SONAR_TOKEN, SONAR_HOST_URL         # SonarQube
DEPLOY_SSH_KEY                      # SSH deployment
```

See the [Migration README](.github/ci-archive/MIGRATION-README.md) for complete list.

## Original Jenkins Examples (Archived)

Original Jenkins pipeline files have been preserved in `.github/ci-archive/`:

* **declarative-examples/** - Declarative pipeline syntax examples
* **jenkinsfile-examples/** - Real-world Jenkinsfile examples
* **pipeline-examples/** - Scripted pipeline examples (24+ examples)
* **global-library-examples/** - Shared library examples

**Total:** 53 Jenkins pipeline files archived

## Migration Details

- ✅ All 53 Jenkins files migrated to 10 GitHub Actions workflows
- ✅ Validated with actionlint (0 errors)
- ✅ Shared libraries expanded inline
- ✅ Plugin equivalents documented

[📖 Read the complete migration guide](.github/ci-archive/MIGRATION-README.md)

## Resources

### GitHub Actions Documentation
- [GitHub Actions Overview](https://docs.github.com/en/actions)
- [Workflow Syntax](https://docs.github.com/en/actions/reference/workflow-syntax-for-github-actions)
- [Migrating from Jenkins](https://docs.github.com/en/actions/migrating-to-github-actions/migrating-from-jenkins-to-github-actions)

### Jenkins Resources (Original)
- [Jenkins Pipeline Plugin](https://github.com/jenkinsci/workflow-plugin/blob/master/README.md)
- [Pipeline scripts collection of the Docker team](https://github.com/docker/jenkins-pipeline-scripts)
- [Pipeline scripts collection of the Fabric8 team](https://github.com/fabric8io/jenkins-pipeline-library)

## License

All contributions are under the MIT license, like Jenkins itself.
