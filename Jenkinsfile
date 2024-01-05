pipeline {
    agent any
    environment {
        // Define environment variables
        GITHUB_REPO = 'https://github.com/Tuhin810/chatApp_cicd.git'
        DOCKER_IMAGE_NAME = 'your_docker_image_name'
        DOCKERHUB_USERNAME = 'tuhin08'
        DOCKERHUB_PASSWORD = 'S#@gFFB_cW.Bw35'
    }
    stages {
        stage('Clone from GitHub') {
            steps {
                echo "Clone the repository from GitHub"
                git url: GITHUB_REPO , branch: "main"
              
            }
        }

        stage('Build Docker Image') {
            steps {
                echo "Build the Docker image"
                sh "docker build -t starmarkbackend ." 
               
            }
        }

        stage('Push to Docker Hub') {
            steps {
                // Log in to Docker Hub
                echo "Log in to Docker Hub"
                sh "docker tag starmarkbackend tuhin08/starmarkbackend:latest"
                sh "docker login -u tuhin08 -p S#@gFFB_cW.Bw35"
                sh "docker push tuhin08/starmarkbackend:latest"
            }
        }

        stage('Run Docker Image') {
            steps {
                // Run the Docker image
                echo "Run the Docker image"
                sh "docker-compose down && docker-compose up -d"

            }
        }
    }
}
