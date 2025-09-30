pipeline {
    agent any

    tools {
        jdk 'Java-17'
        maven 'Maven-3.9'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }

        stage('Deploy to Nexus') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'nexus-creds', usernameVariable: 'NEXUS_USER', passwordVariable: 'NEXUS_PASS')]) {
                    bat """
                        mvn deploy -Dnexus.username=%NEXUS_USER% -Dnexus.password=%NEXUS_PASS%
                    """
                }
            }
        }
    }
}
