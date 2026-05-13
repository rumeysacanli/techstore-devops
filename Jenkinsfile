pipeline {
    agent any
    stages {
        stage('Dosyayi Bul ve Test Et') {
            steps {
                checkout scm
                script {
                    // requirements.txt dosyasının nerede olduğunu otomatik buluyoruz
                    def findPath = sh(script: "find . -name requirements.txt", returnStdout: true).trim()
                    def dirPath = findPath.replace('/requirements.txt', '')
                    
                    echo "Dosyalar burada bulundu: ${dirPath}"
                    
                    dir("${dirPath}") {
                        sh 'python3 -m venv venv'
                        sh './venv/bin/pip install -r requirements.txt'
                        sh './venv/bin/pytest tests/test_app.py -v'
                    }
                }
            }
        }
    }
}
