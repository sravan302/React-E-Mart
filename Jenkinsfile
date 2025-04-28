pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git branch: 'main', url: 'https://github.com/sravan302/React-E-Mart.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }
        stage('Build React App') {
            steps {
                sh 'npm run build'
            }
        }
        stage('Docker Build') {
            steps {
                sh 'docker build -t emart-react-app .'
            }
        }
        stage('Docker Run') {
            steps {
                sh 'docker run -d -p 3000:80 emart-react-app'
            }
        }
    }
}
