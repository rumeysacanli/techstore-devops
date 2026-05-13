pipeline {
    agent any
    stages {
        stage('Hazirlik ve Test') {
            steps {
                checkout scm
                // Jenkins'e tam olarak 3 kat içeri girmesini söylüyoruz
                dir('techstore-devops/techstore-devops/techstore-devops') { 
                    sh 'python3 -m venv venv'
                    sh './venv/bin/pip install -r requirements.txt'
                    sh './venv/bin/pytest tests/test_app.py -v'
                }
            }
        }
        stage('Final Başarı') {
            steps {
                echo 'pepline başarılı '
            }
        }
    }
}
