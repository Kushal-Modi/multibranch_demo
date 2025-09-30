pipeline {
    agent any

    tools {
        maven 'Maven-3.9'   // Make sure this name matches Jenkins Maven installation
        jdk 'Java-17'       // Make sure this matches Jenkins JDK installation
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
    }
}
