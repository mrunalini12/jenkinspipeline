pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building Docker image...'
                sh 'docker build -t jenkins-cicd-app .'
            }
        }

        stage('Test') {
            steps {
                echo 'Running basic test...'
                sh 'test -f index.html && echo "✅ index.html exists!" || echo "❌ index.html missing!"'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying Docker container...'
                sh 'docker rm -f jenkins-cicd-container || true'
                sh 'docker run -d -p 8081:80 --name jenkins-cicd-container jenkins-cicd-app'
            }
        }
    }
}
