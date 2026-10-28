pipeline {
    agent any

    stages {
        stage('Verification Python') {
            steps {
                sh 'python3 --version'
            }
        }

        stage('Installation des dependances') {
            steps {
                sh '''
                    python3 -m venv .venv
                    .venv/bin/python -m pip install -r requirements.txt
                    .venv/bin/python -m pip install pytest
                '''
            }
        }

        stage('Tests automatiques') {
            steps {
                sh '.venv/bin/python -m pytest -v'
            }
        }
    }
}
