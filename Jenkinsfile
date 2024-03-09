pipeline {
    agent {
        docker {
            image 'python:3.8'
        }
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                    git branch: 'main', url: 'https://github.com/kazim-asif/20i2310-task2.git'
                }
            }
        }

        stage('Environment preparation - Install Dependencies') {
            steps {
                echo "-=- preparing project environment -=-"
                // Python dependencies
                sh "pip install -r requirements.txt"
            }
        }

        stage('Run Tests') {
            steps {
                script {
                     echo "-=- execute tests -=-"
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
