pipeline {
    agent any

    parameters {
        choice(
            name: 'ENVIRONNEMENT',
            choices: ['dev', 'recette', 'production'],
            description: 'Choisir l environnement'
        )

        booleanParam(
            name: 'EXECUTER_TESTS',
            defaultValue: true,
            description: 'Executer les tests automatiques'
        )
    }

    stages {
        stage('Preparation') {
            steps {
                echo "Environnement choisi : ${params.ENVIRONNEMENT}"
                echo "Executer les tests : ${params.EXECUTER_TESTS}"
            }
        }

        stage('Installation des dependances') {
            when {
                expression { params.EXECUTER_TESTS }
            }

            steps {
                sh '''
                    python3 -m venv .venv
                    .venv/bin/python -m pip install -r requirements.txt
                    .venv/bin/python -m pip install pytest
                '''
            }
        }

        stage('Tests automatiques') {
            when {
                expression { params.EXECUTER_TESTS }
            }

            steps {
                sh '.venv/bin/python -m pytest -v'
            }
        }
    }
}
