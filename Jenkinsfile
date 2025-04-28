pipeline {
    agent any

    stages {
        stage('Checkout SCM') {
            steps {
                git 'https://github.com/sravan302/React-E-Mart.git'
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
                sh 'docker build -t react-e-mart-app .'
            }
        }

        stage('Docker Run') {
            steps {
                sh 'docker run -d -p 80:80 --name react-e-mart-container react-e-mart-app'
            }
        }
    }
}
