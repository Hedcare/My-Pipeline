Jenkinsfile (Declarative Pipeline)
/* Requires the Docker Pipeline plugin */
pipeline {
    agent { docker { image 'maven:3.9.9-eclipse-temurin-21-alpine' } }

    stages {
        stage('Build') {
            steps {
                timeout(time: 20, unit: 'SECONDS') { // Timeout de 20 segundos
                    retry(3) { // Reintenta hasta 3 veces si falla
                        sh 'mvn --version'
                    }
                }
            }
        }

        stage('Compile') {
            steps {
                timeout(time: 15, unit: 'SECONDS') { // Timeout de 15 segundos
                    retry(2) { // Reintenta hasta 2 veces si falla
                        sh 'mvn clean compile'
                    }
                }
            }
        }

        stage('Test') {
            steps {
                timeout(time: 15, unit: 'SECONDS') { // Timeout de 15 segundos
                    retry(2) { // Reintenta hasta 2 veces si falla
                        sh 'mvn test'
                    }
                }
            }
        }
    }
}
