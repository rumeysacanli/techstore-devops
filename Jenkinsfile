pipeline {
    agent any
    stages {
        stage('Hazirlik ve Kurulum') {
            steps {
                checkout scm
                script {
                    def findPath = sh(script: "find . -name requirements.txt", returnStdout: true).trim()
                    def dirPath = findPath.replace('/requirements.txt', '')
                    
                    dir("${dirPath}") {
                        sh 'python3 -m venv venv'
                        sh './venv/bin/pip install -r requirements.txt'
                        // Testleri koştururken bulunduğumuz dizini Python'a tanıtıyoruz
                        sh 'PYTHONPATH=. ./venv/bin/pytest tests/test_app.py -v'
                    }
                }
            }
        }
        stage('Basari') {
            steps {
                echo 'Pipeline Tamamlandi.'
            }
        }
    }
}
