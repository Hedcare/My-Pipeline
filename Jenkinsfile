pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'my-java-app:latest'  // Nombre de la imagen Docker
        DOCKERFILE_PATH = '.'  // Directorio donde se encuentra el Dockerfile
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Clonando el repositorio...'
                // Aquí iría el comando de checkout si fuera real
                // checkout scm
            }
        }
        
        stage('Build') {
            steps {
                echo 'Compilando la aplicación Java...'
                // Simulación de la compilación sin ejecutar realmente
                // sh 'mvn clean package'  // Reemplázalo por 'gradle build' si usas Gradle
            }
        }

        stage('Build Docker Image') {
            steps {
                echo 'Construyendo la imagen Docker...'
                // Simulación de la construcción de la imagen Docker
                // sh 'docker build -t ${DOCKER_IMAGE} ${DOCKERFILE_PATH}'
            }
        }

        stage('Run Tests') {
            steps {
                echo 'Ejecutando pruebas dentro del contenedor Docker...'
                // Simulación de la ejecución de pruebas
                // sh 'docker run --rm ${DOCKER_IMAGE} mvn test'
            }
        }

        stage('Cleanup') {
            steps {
                echo 'Limpiando recursos Docker...'
                // Simulación de limpieza
                // sh 'docker rmi ${DOCKER_IMAGE}'
            }
        }
    }

    post {
        always {
            echo 'Este paso se ejecuta siempre, independientemente del resultado.'
            // Aquí puedes agregar acciones que se ejecuten siempre
        }
    }
}
