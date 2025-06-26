# 🚀 Java CI/CD Pipeline with Jenkins, Maven & Nexus

This project demonstrates a complete DevOps pipeline to automate the build and deployment of a Java-based application using **Jenkins**, **Maven**, **Docker**, and **Sonatype Nexus Repository**.

> ✅ Ideal for understanding end-to-end automation of a `.jar` deployment workflow from source code to artifact repository.

---

## 📁 Project Overview

- **Language:** Java (Maven)
- **Build Tool:** Apache Maven
- **CI/CD Tool:** Jenkins
- **Artifact Repository:** Sonatype Nexus
- **Containerization:** Docker

---

## 🎯 Objectives

- Automate build, test, and deployment process of a Java application.
- Use Jenkins Pipeline (`Jenkinsfile`) to manage CI/CD steps.
- Deploy `.jar` artifacts to a private Nexus Repository using Maven.

---

## 🔧 Tools & Technologies

| Tool       | Purpose                         |
|------------|----------------------------------|
| Java       | Application source code          |
| Maven      | Build and dependency management  |
| Jenkins    | CI/CD automation                 |
| Docker     | Containerization of Jenkins & Nexus |
| Nexus      | Artifact repository management   |
| Git/GitHub | Source code management           |

---

## 📦 Pipeline Workflow

```mermaid
graph LR
A[GitHub Push] --> B[Jenkins Pipeline Trigger]
B --> C[Build with Maven]
C --> D[Generate .jar File]
D --> E[Deploy to Nexus Reposito

## 🛠️ Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/aradhya-7-7/GreetingApp.git
cd GreetingApp
```

### 2. Docker Setup

Start Jenkins and Nexus using Docker:

```bash
# Jenkins
docker run -d -p 8080:8080 -p 50000:50000 --name jenkins \
  -v jenkins_home:/var/jenkins_home \
  -v /var/run/docker.sock:/var/run/docker.sock \
  jenkins/jenkins:lts

# Nexus
docker run -d -p 8081:8081 --name nexus sonatype/nexus3
```

### 3. Retrieve Jenkins and Nexus Credentials

```bash
docker exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword
docker exec nexus cat /nexus-data/admin.password
```

---

## 📝 Jenkinsfile

This file defines the pipeline stages:

```groovy
pipeline {
  agent any
  tools {
    maven 'Maven 3.9.10'
    jdk 'Java 21'
  }
  stages {
    stage('Build') {
      steps {
        bat 'mvn clean package'
      }
    }
    stage('Deploy to Nexus') {
      steps {
        bat 'mvn deploy --settings settings.xml'
      }
    }
  }
}
```

---

## ⚙️ Maven Configuration (`pom.xml`)

Configured with `distributionManagement` to deploy artifacts:

```xml
<distributionManagement>
  <repository>
    <id>nexus</id>
    <url>http://localhost:8081/repository/maven-releases/</url>
  </repository>
</distributionManagement>
```

And credentials in `settings.xml`.

---

## 📂 Directory Structure

```
GreetingApp/
├── src/
│   └── main/java/com/example/Greeting.java
├── pom.xml
├── Jenkinsfile
├── settings.xml
└── README.md
```

---

## ✅ Sample Output

* ✔️ Jenkins Build: `BUILD SUCCESS`
* ✔️ Nexus Upload: `.jar` visible in `maven-releases`
* ✔️ GitHub Integration Working

---

## 📸 Screenshots

* Jenkins pipeline execution
![Alttext](src\images\pipeline_overview.png)
* Nexus showing uploaded `.jar`
![Alttext](src\images\jaroverview.png)

---

## 📚 Skills Demonstrated

* CI/CD pipeline design and automation
* Jenkins pipeline scripting with Maven
* Artifact deployment to Nexus
* Docker container orchestration
* Maven project management and build lifecycle
* Secure credential and repository management

---

## 🔗 Useful Resources

* [Jenkins Documentation](https://www.jenkins.io/doc/)
* [Maven Deploy Plugin](https://maven.apache.org/plugins/maven-deploy-plugin/)
* [Sonatype Nexus Docs](https://help.sonatype.com/repomanager3)

---

## ✨ Author

**Aradhya Srivastava**
*Fresher Software Developer passionate about DevOps and Full-Stack Engineering*
🔗 [GitHub](https://github.com/aradhya-7-7)
