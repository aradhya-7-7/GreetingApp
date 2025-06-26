pipeline {
    agent any

    tools {
        maven 'maven'   // match your Maven install name
        jdk 'JDK21'      // match your JDK install name exactly
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
