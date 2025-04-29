pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/sravan302/React-E-Mart.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t sravan302/react-e-mart:latest .'
            }
        }

        stage('Deploy to EC2 Ubuntu') {
            steps {
                sshagent(['ec2-ssh-credentials']) {
                    sh '''
                        ssh -o StrictHostKeyChecking=no ubuntu@43.204.215.117 << 'EOF'
                        docker pull sravan302/react-e-mart:latest || true
                        docker stop react-e-mart || true
                        docker rm react-e-mart || true
                        docker run -d --name react-e-mart -p 80:80 sravan302/react-e-mart:latest
                        EOF
                    '''
                }
            }
        }
    }
}
