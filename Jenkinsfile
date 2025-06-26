pipeline {
    agent any

    tools {
    maven 'maven'       // change to actual tool name from Jenkins UI
    jdk 'jdk'           // also match the existing JDK name
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
