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
                echo 'Deploying...'
                // Add deployment commands here
            }
        }
    }
}
