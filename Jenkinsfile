pipeline {
    agent any

    tools {
        nodejs "Node18" // Configura una instalación de Node.js en Jenkins
        dockerTool "Dockertool"  // Cambia el nombre de la herramienta según tu configuración en Jenkins
    }
    environment {
        DOCKER_API_VERSION = '1.40' // Establece la versión de la API de Docker
    }

    stages {
        stage('Construir Imagen Docker') {
            steps {
                sh 'docker build -t hola-mundo-node:latest .'
            }
        }

        stage('Ejecutar Contenedor Node.js') {
            steps {
                sh '''
                    # Detener y eliminar cualquier contenedor previo
                    docker stop hola-mundo-node || true
                    docker rm hola-mundo-node || true

                    # Ejecutar el contenedor de la aplicación
                    docker run -d --name hola-mundo-node -p 3838:3838 hola-mundo-node:latest
                '''
            }
        }
    }
}