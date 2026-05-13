pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // GitHub'dan kodları çekme aşaması
                checkout scm
            }
        }

        stage('Setup') {
            steps {
                // Python ortamını hazırlama
                sh 'python3 -m venv venv'
                sh '. venv/bin/activate && pip install -r requirements.txt'
            }
        }

        stage('Unit Tests') {
            steps {
                // 30 adet testi koşturma aşaması
                sh '. venv/bin/activate && pytest tests/test_app.py -v'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                // Kod kalite analizi
                script {
                    def scannerHome = tool 'SonarQube'
                    withSonarQubeEnv('SonarQube') {
                        sh "${scannerHome}/bin/sonar-scanner"
                    }
                }
            }
        }

        stage('Docker Build') {
            steps {
                // Uygulamanın Docker imajını oluşturma
                sh 'docker build -t techstore-app:latest .'
            }
        }

        stage('Deploy') {
            steps {
                // Yeni container'ı ayağa kaldırma
                sh 'docker-compose up -d'
            }
        }
    }
}
