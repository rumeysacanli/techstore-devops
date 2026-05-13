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
                // Klasörün içine girip işlemleri orada yapıyoruz
                sh 'python3 -m venv venv'
                sh './venv/bin/pip install -r techstore-devops/requirements.txt'
                sh './venv/bin/pytest techstore-devops/tests/test_app.py -v'
            }
        }
        stage('Final') {
            steps {
                echo 'Pepline başarılı'
            }
        }
    }
}
