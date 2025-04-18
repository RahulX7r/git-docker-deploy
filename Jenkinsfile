pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git url: 'https://github.com/your-user/your-flask-repo.git', branch: 'main'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build('flask-app')
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    sh 'docker stop flask-app || true'
                    sh 'docker rm flask-app || true'
                    sh 'docker run -d -p 5000:5000 --name flask-app flask-app'
                }
            }
        }
    }
}
