pipeline {
    agent any

    tools {
        maven 'Maven3'
        jdk 'JDK21'
    }

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Deploy to Nexus') {
            steps {
                sh 'mvn deploy --settings settings.xml'
            }
        }
    }
}
