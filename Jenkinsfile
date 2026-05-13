pipeline {
    agent any
    stages {
        stage('Hazırlık') {
            steps {
                checkout scm
            }
        }
        stage('Testleri Koştur') {
            steps {
                sh 'python3 -m venv venv'
                sh './venv/bin/pip install -r requirements.txt'
                sh './venv/bin/pytest tests/test_app.py -v'
            }
        }
        stage('Final') {
            steps {
                echo 'Pipeline başarıyla tamamlandı!'
            }
        }
    }
}
