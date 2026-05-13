pipeline {
    agent any
    stages {
        stage('Dosyalari Listele') {
            steps {
                // Jenkins şu an nerede ve içinde ne var, hepsini göreceğiz
                sh 'ls -R' 
            }
        }
        stage('Test') {
            steps {
                // Eğer requirements.txt dosyan direkt ana dizindeyse bu komut çalışacak
                sh 'python3 -m venv venv'
                sh './venv/bin/pip install -r requirements.txt || ./venv/bin/pip install -r techstore-devops/techstore-devops/requirements.txt'
                sh './venv/bin/pytest tests/test_app.py -v || ./venv/bin/pytest techstore-devops/techstore-devops/tests/test_app.py -v'
            }
        }
    }
}
