pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/utkiya/blinkit_clone.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t blinkit_clone .'
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    sh 'docker run -d -p 8080:80 --name blinkit_clone_container blinkit_clone'
                }
            }
        }

        stage('Post-Build Cleanup') {
            steps {
                sh 'docker image prune -f'
            }
        }
    }
}
