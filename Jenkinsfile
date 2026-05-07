pipeline {
    agent any

    tools {
        maven 'Maven3'
        jdk 'JDK17'
    }

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/neetha5/openEnd.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Package') {
            steps {
                sh 'mvn package'
            }
        }
    post {

        success {
            emailext (
                subject: "SUCCESS: ${JOB_NAME} #${BUILD_NUMBER}",
                body: "Build succeeded!\nCheck: ${BUILD_URL}",
                to: "neethacn2004@gmail.com"
            )
        }

        failure {
            emailext (
                subject: "FAILED: ${JOB_NAME} #${BUILD_NUMBER}",
                body: "Build failed!\nCheck: ${BUILD_URL}",
                to: "neethacn2004@gmail.com"
            )
        }
    }
}
