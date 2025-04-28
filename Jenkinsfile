pipeline {
    agent any

    environment {
        IMAGE_NAME = "Lucky143/emart-react-app"
    }

    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/sravan302/React-E-Mart.git'
            }
        }

        stage('Build React App') {
            steps {
                sh 'npm install'
                sh 'npm run build'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh "docker build -t $IMAGE_NAME ."
            }
        }

        stage('Run Docker Container') {
            steps {
                sh "docker run -d -p 3000:80 --name emart-container $IMAGE_NAME"
            }
        }
    }
}
