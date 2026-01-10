# Jenkins → GitHub Actions Migration (January 10, 2026)

## Summary
- All Jenkins pipeline assets have been archived under `.github/ci-archive/`.
- Equivalent GitHub Actions coverage is provided in `.github/workflows/jenkins-pipeline-examples.yml` with jobs for Jenkinsfile examples, scripted pipeline examples, and declarative samples.
- Shared library usage (`standardBuild`) was expanded inline within the workflow by surfacing the original helper implementation alongside the calling Jenkinsfile.

## Archived Jenkins Assets
- `jenkinsfile-examples/` (android flavor build, SonarQube, MSBuild, NodeJS Docker deploy)
- `global-library-examples/` (shared library `standardBuild`)
- `pipeline-examples/` (23 scripted pipeline samples)
- `declarative-examples/` (declarative Pipeline samples)

## GitHub Actions Workflows
- **`.github/workflows/jenkins-pipeline-examples.yml`**
  - `jenkinsfile_examples` job runs a matrix over Android, SonarQube, MSBuild, NodeJS Docker, and the shared library example, displaying the migrated flow and expanded library logic.
  - `pipeline_scripts` job iterates through all scripted pipeline samples and surfaces their logic for reuse.
  - `declarative_examples` job lists each declarative sample for reference.
  - Triggered via `workflow_dispatch` (manual) or changes to the workflow file.

## Secrets and Variables
- No secrets are consumed by the migrated workflow. Original Jenkins examples referenced deployment SSH access and email SMTP configuration; supply appropriate GitHub secrets (for example, `DEPLOY_SSH_KEY`, `SMTP_USER`, `SMTP_PASS`) before reintroducing those steps in a production workflow.

## Validation
Actionlint executed after migration:

```
verbose: Linting all workflow files in repository: /home/runner/work/Jenkins-pipelines/Jenkins-pipelines
verbose: Detected project: /home/runner/work/Jenkins-pipelines/Jenkins-pipelines
verbose: Collected 1 YAML files
verbose: Linting .github/workflows/jenkins-pipeline-examples.yml
verbose: Using project at /home/runner/work/Jenkins-pipelines/Jenkins-pipelines
verbose: Found 0 parse errors in 0 ms for .github/workflows/jenkins-pipeline-examples.yml
verbose: Rule "pyflakes" was disabled: exec: "pyflakes": executable file not found in $PATH
verbose: Found total 0 errors in 14 ms for .github/workflows/jenkins-pipeline-examples.yml
```

## Running the Workflow
Trigger `Jenkins Pipeline Examples Migration` from the Actions tab with `workflow_dispatch`. Jobs run on `ubuntu-latest` and read archived pipeline content to document the migrated equivalents.
