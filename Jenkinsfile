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
                // Sanal ortam oluşturup paketleri onun içine yüklüyoruz (En güvenli yol)
                sh 'python3 -m venv venv'
                sh './venv/bin/pip install --upgrade pip'
                sh './venv/bin/pip install -r requirements.txt'
                sh './venv/bin/pytest tests/test_app.py -v'
            }
        }
        stage('Docker Build') {
            steps {
                // Uygulamanın Docker imajını oluşturma aşaması
                sh 'docker build -t techstore-app:latest .' [cite: 61]
            }
        }
    }
}
