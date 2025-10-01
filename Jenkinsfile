@Library('jenkins-shared-lib') _

pipeline {
    agent any

    stages {
        stage('Greet') {
            steps {
                sayHello('Kushal')
            }
        }

        stage('Build') {
            steps {
                echo "Building Job Portal project..."
                // bat 'mvn clean install'   // Uncomment if Maven installed
            }
        }

        stage('Test') {
            steps {
                echo "Running tests..."
                // bat 'mvn test'
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying application..."
                // bat './deploy.sh'
            }
        }
    }
}
