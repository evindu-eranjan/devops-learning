
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out source code...'
                checkout scm
            }
        }

        stage('Setup Python') {
            steps {
                echo 'Creating Python virtual environment...'
                sh '''
                    python3 -m venv venv
                    . venv/bin/activate
                    python -m pip install pytest
                '''
            }
        }

        stage('Run Tests') {
            steps {
                echo 'Running Python tests...'
                sh '''
                    . venv/bin/activate
                    python -m pytest tests/ -v
                '''
            }
        }
    }

    post {
        success {
            echo 'All tests passed!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}

