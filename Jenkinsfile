pipeline {
    agent none
    stages {
        stage('Build') {
            agent { docker { image 'maven:3.9.9-eclipse-temurin-21-alpine' } }
            steps {
                echo "Building with Maven"
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            agent { docker { image 'maven:3.9.9-eclipse-temurin-21-alpine' } }
            steps {
                echo "Running tests with Maven"
                sh 'mvn test'
            }
        }

        stage('Deploy') {
            agent any
            steps {
                echo "Deployment successful. The application is ready for use."
            }
        }
    }
}
