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
                        mvn deploy -Dnexus.user=%NEXUS_USER% -Dnexus.password=%NEXUS_PASS%
                    """
                }
            }
        }
    }
}
