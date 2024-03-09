pipeline {
    agent any

    tools {
        // Define the Python tool with the desired version
        python 'Python3.8'
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
                    // Use the 'python' tool to install dependencies
                    bat "\"${tool 'Python3.8'}\" -m pip install -r requirements.txt"
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    // Use the 'python' tool to run pytest
                    bat "\"${tool 'Python3.8'}\" -m pytest test.py"
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
