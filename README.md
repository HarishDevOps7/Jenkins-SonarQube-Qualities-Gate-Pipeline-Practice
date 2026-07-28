# Jenkins + SonarQube Quality Gate Pipeline

## 📌 Project Overview

This project demonstrates how to integrate **SonarQube** with a **Jenkins Continuous Integration (CI) Pipeline** to automate code quality analysis. The pipeline performs source code checkout, builds the application, executes static code analysis using SonarQube, and evaluates the project against predefined Quality Gates. This implementation helps maintain high code quality by detecting bugs, vulnerabilities, code smells, and other maintainability issues before deployment.

---

## 🎯 Objectives

- Integrate SonarQube with Jenkins.
- Automate static code analysis.
- Configure SonarQube Quality Gates.
- Build Java applications using Maven.
- Perform automated code quality checks.
- Improve code reliability and maintainability.

---

## 🏗️ Architecture

The CI pipeline consists of the following components:

- **GitHub Repository** – Stores the application source code and Jenkinsfile.
- **Jenkins** – Automates the CI pipeline.
- **SonarQube Server** – Performs static code analysis.
- **Maven** – Builds the Java application.
- **Quality Gate** – Validates code quality before pipeline completion.

---

## 🛠️ Technologies Used

- Jenkins
- SonarQube
- SonarQube Scanner
- GitHub
- Git
- Java
- Apache Maven
- Jenkins Pipeline
- Declarative Jenkinsfile

---

## 📂 Project Structure

```text
Jenkins-SonarQube-Qualities-Gate-Pipeline/
│
├── Screenshots/
│
├── src/
│
├── Jenkinsfile
├── pom.xml
├── sonar-project.properties
└── README.md
```

---

## 🚀 Implementation Steps

### 1. Configure SonarQube Server

- Install SonarQube.
- Start the SonarQube Server.
- Generate a SonarQube Authentication Token.
- Configure the SonarQube Server URL in Jenkins.

Example:

```text
http://localhost:9000
```

---

### 2. Configure Jenkins

Install the required plugins:

- SonarQube Scanner Plugin
- Pipeline Plugin
- Git Plugin

Configure:

- SonarQube Server
- Authentication Token
- Maven
- JDK

---

### 3. Configure Repository

Store the following files in the GitHub repository:

- Java Source Code (`src/`)
- `pom.xml`
- `sonar-project.properties`
- `Jenkinsfile`

---

### 4. Create Jenkins Pipeline

Create a Pipeline Job using:

- Pipeline script from SCM
- Git Repository
- Jenkinsfile

---

### 5. Execute the Pipeline

The pipeline executes the following stages:

- Checkout
- Build
- SonarQube Analysis
- Quality Gate Verification

---

## 🔄 Jenkinsfile

```groovy
pipeline {

    agent any

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/ManojKumar8244/Jenkins-SonarQube-Qualities-Gate-Pipeline.git'
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
```

---

## 🔍 Verification Commands

### Build the Project

```bash
mvn clean package
```

### Run SonarQube Analysis

```bash
mvn sonar:sonar
```

### Verify Generated Artifact

```bash
ls target/
```

---

## 📊 Key Features

- Jenkins CI Pipeline
- SonarQube Integration
- Automated Static Code Analysis
- Quality Gate Enforcement
- Pipeline as Code
- GitHub Integration
- Maven Build Automation
- Continuous Code Quality Monitoring

---

## 📚 Learning Outcomes

Through this project, I gained hands-on experience with:

- Jenkins Pipeline
- SonarQube
- SonarQube Scanner
- Static Code Analysis
- Quality Gates
- Maven Build Automation
- Continuous Integration (CI)
- Code Quality Management

---

## 📸 Screenshots

Include screenshots of:

- Jenkins Dashboard
- Jenkins Pipeline Configuration
- Successful Pipeline Execution
- SonarQube Dashboard
- SonarQube Project Overview
- Quality Gate Status
- Issues Report (Bugs, Vulnerabilities, Code Smells)
- Jenkins Console Output

---

## ✅ Project Outcome

Successfully integrated SonarQube with a Jenkins CI pipeline to automate static code analysis and enforce Quality Gates. The pipeline automatically checks code quality during the build process, providing immediate feedback on bugs, vulnerabilities, code smells, and maintainability issues. This project demonstrates DevOps best practices for implementing continuous code quality inspection and maintaining high software quality standards.

---

## 👨‍💻 Author

**Manoj Kumar**

- GitHub: https://github.com/ManojKumar8244
