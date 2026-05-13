pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Setup & Test') {
            steps {
                // Karmaşık venv işlemleri yerine doğrudan paketleri yükleyip test ediyoruz
                sh 'pip install --upgrade pip'
                sh 'pip install -r requirements.txt'
                sh 'pytest tests/test_app.py -v'
            }
        }
        stage('Docker Build') {
            steps {
                sh 'docker build -t techstore-app:latest .'
            }
        }
    }
}
