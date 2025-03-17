pipeline {
    agent none
    options {
        timeout(time: 30, unit: 'SECONDS') // Timeout global de 30 segundos
    }
    stages {
        stage('Build') {
            agent { docker { image 'maven:3.9.9-eclipse-temurin-21-alpine' } }
            steps {
                timeout(time: 20, unit: 'SECONDS') { // Timeout de 20 segundos en esta etapa
                    retry(3) { // Reintenta hasta 3 veces si falla
                        sh 'mvn --version'
                    }
                }
            }
        }

        stage('Compile') {
            agent { docker { image 'maven:3.9.9-eclipse-temurin-21-alpine' } }
            steps {
                timeout(time: 15, unit: 'SECONDS') { // Timeout de 15 segundos
                    retry(2) { // Reintenta hasta 2 veces si falla
                        sh 'mvn clean compile'
                    }
                }
            }
        }

        stage('Test') {
            agent { docker { image 'maven:3.9.9-eclipse-temurin-21-alpine' } }
            steps {
                timeout(time: 15, unit: 'SECONDS') { // Timeout de 15 segundos
                    retry(2) { // Reintenta hasta 2 veces si falla
                        sh 'mvn test'
                    }
                }
            }
        }

        stage('Input') {
            agent any
            input {
                message "What is your first name?"
                ok "Submit"
                parameters {
                    string(defaultValue: 'Dave', name: 'FIRST_NAME', trim: true)
                }
            }
            options {
                timeout(time: 10, unit: 'SECONDS') // Timeout en la etapa de input
            }
            steps {
                echo "Good Morning, $FIRST_NAME"
                sh '''
                  hostname
                  cat /etc/redhat-release
                '''
            }
        }
    }
}
