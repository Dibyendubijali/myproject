pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/Dibyendubijali/myproject.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("flask-app")
                }
            }
        }
        stage('Run Tests') {
            steps {
                // If you have tests, run them here
                echo 'No tests defined yet'
            }
        }
        stage('Deploy') {
            steps {
                script {
                    // Stop old container if exists
                    sh 'docker stop flask-app || true'
                    sh 'docker rm flask-app || true'
                    // Run new container
                    sh 'docker run -d -p 5000:5000 --name flask-app flask-app'
                }
            }
        }
    }
}

