pipeline {
    agent any

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
                    // Use the 'withPythonEnv' step to manage Python environment
                    withPythonEnv('Python3.8') {
                        bat "pip install -r requirements.txt"
                    }
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    // Use the 'withPythonEnv' step to manage Python environment
                    withPythonEnv('Python3.8') {
                        bat "pytest test.py"
                    }
                }
            }
        }
    }

    post {
        success {
            echo 'Job successful! Running additional tasks...'
            // Add any post-build tasks or notifications here
        }

        failure {
            echo 'Job failed! Sending notifications...'
            // Add any failure notifications or cleanup tasks here
        }
    }
}
