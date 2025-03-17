pipeline {
    agent none
    options {
        timeout(time: 30, unit: 'SECONDS') // Timeout global de 30 segundos
    }
    environment {
        JAVA_HOME = '/usr/lib/jvm/java-21-openjdk'
        USER_NAME = 'jenkins_user'
    }
    stages {
        stage('Build') {
            agent { docker { image 'maven:3.9.9-eclipse-temurin-21-alpine' } }
            steps {
                echo "Building with JAVA_HOME=$JAVA_HOME"
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            agent { docker { image 'maven:3.9.9-eclipse-temurin-21-alpine' } }
            steps {
                echo "Running tests with JAVA_HOME=$JAVA_HOME"
                sh 'mvn test'
            }
            post {
                always {
                    archiveArtifacts artifacts: '**/target/*.jar', allowEmptyArchive: true
                    echo "Test results and artifacts have been archived"
                }
            }
        }

        stage('Deploy') {
            agent any
            steps {
                echo "Deploying application..."
                sh 'echo Deploy step executed'
            }
        }
    }
}
