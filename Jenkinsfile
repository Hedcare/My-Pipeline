pipeline {
    agent {
        docker {
            image 'maven:3.9.9-eclipse-temurin-21-alpine'
            args '-v /C/ProgramData/Jenkins:/mnt'  // Usa una ruta absoluta en Windows
            workDir '/mnt/workspace'  // Cambia el directorio de trabajo a una ruta absoluta
        }
    }
    stages {
        stage('Build') {
            steps {
                echo "Building with Maven"
                sh 'mvn clean install'
            }
        }
        stage('Test') {
            steps {
                echo "Running tests with Maven"
                sh 'mvn test'
            }
        }
        stage('Deploy') {
            steps {
                echo "Deployment successful."
            }
        }
    }
}
