pipeline {
    agent any

    tools {
        maven 'Maven3'   // match your Maven install name
        jdk 'JDK21'      // match your JDK install name exactly
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
