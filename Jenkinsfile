pipeline {
    agent any
    
    environment {
        PYTHON_VERSION = '3.8'
        VIRTUAL_ENV = "${WORKSPACE}\\venv"
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                    git branch: 'main', url: 'https://github.com/kazim-asif/20i2310-task2.git'
                }
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    def pipCmd = "\"${VIRTUAL_ENV}\\Scripts\\pip\""
                    bat "${pipCmd} install -r requirements.txt"
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    def pytestCmd = "\"${VIRTUAL_ENV}\\Scripts\\pytest\""
                    bat "${pytestCmd} test.py"
                }
            }
        }
    }

    post {
        success {
            echo 'Build successful! Running additional tasks...'
            // Add any post-build tasks or notifications here
        }

        failure {
            echo 'Build failed! Sending notifications...'
            // Add any failure notifications or cleanup tasks here
        }
    }
}
