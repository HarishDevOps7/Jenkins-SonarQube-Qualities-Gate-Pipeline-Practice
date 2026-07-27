# Jenkins + SonarQube Quality Gate Pipeline

## Problem Statement Overview
As software projects scale, codebases accumulate issues such as code smells, security vulnerabilities, bugs, and low test coverage. Manual code reviews fail to detect all issues reliably. Integrating SonarQube into the CI pipeline automates code quality analysis and enforces Quality Gates, ensuring that only code meeting security and quality standards passes the pipeline.

## Solution Approach
I integrated SonarQube with a Jenkins CI pipeline to automate continuous code inspection:
1. **SonarQube Integration:** Installed SonarQube Server and configured the SonarQube Scanner plugin in Jenkins using authentication tokens.
2. **Project Configuration:** Defined project metadata in `sonar-project.properties` and structured the Java Maven application.
3. **Pipeline as Code:** Created a `Jenkinsfile` utilizing the `withSonarQubeEnv` block to trigger static code scanning during the build.
4. **Quality Gate Verification:** Evaluated code against SonarQube quality gates (Bugs, Vulnerabilities, Code Smells, Coverage) to provide immediate feedback on code quality.

## Dependencies and Tools
* Jenkins CI Server
* SonarQube Server (`http://localhost:9000`)
* SonarQube Scanner Plugin for Jenkins
* GitHub Repository
* Java & Apache Maven
* `sonar-project.properties` Configuration File

## Execution Steps

### 1. SonarQube & Jenkins Integration Setup
1. Launch SonarQube server and generate an Authentication Token from the SonarQube dashboard.
2. Install the **SonarQube Scanner Plugin** in Jenkins via **Manage Jenkins** $\rightarrow$ **Plugins**.
3. Add the SonarQube Server URL and Authentication Token under **Manage Jenkins** $\rightarrow$ **System**.

### 2. Repository & Pipeline Configuration
1. Store application source code (`src/`), Maven configuration (`pom.xml`), and `sonar-project.properties` in GitHub.
2. Add the pipeline definition to `Jenkinsfile`:

```groovy
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git '(https://github.com/ManojKumar8244/Jenkins-SonarQube-Qualities-Gate-Pipeline.git)'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh 'mvn sonar:sonar'
                }
            }
        }
    }
}
