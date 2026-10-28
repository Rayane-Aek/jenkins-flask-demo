pipeline {
    agent any

    stages {
        stage('Verification du code') {
            steps {
                sh 'ls -la'
            }
        }

        stage('Verification Python') {
            steps {
                sh 'python3 --version'
            }
        }
    }
}
