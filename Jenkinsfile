Jenkinsfile (Declarative Pipeline)
/* Requires the Docker Pipeline plugin */
pipeline {
    agent { docker { image 'maven:3.9.9-eclipse-temurin-21-alpine' } }

    stages {
        stage('build') {
            steps {
                timeout(time: 10, unit: 'SECONDS') { // Timeout de 10 segundos
                    retry(3) { // Reintenta hasta 3 veces si falla
                        sh 'mvn --version'
                    }
                }
            }
        }

        stage('test') {
            steps {
                timeout(time: 20, unit: 'SECONDS') { // Timeout de 20 segundos
                    retry(2) { // Reintenta hasta 2 veces si falla
                        sh 'echo Running tests...' // Aquí irían los comandos de prueba
                    }
                }
            }
        }
    }

    post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'This will run only if successful'
        }
        failure {
            echo 'This will run only if failed'
        }
        unstable {
            echo 'This will run only if the run was marked as unstable'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }
    }
}
