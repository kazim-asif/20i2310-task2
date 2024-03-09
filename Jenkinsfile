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

        stage('Set Up Environment') {
            steps {
                script {
                    // Create a virtual environment
                    bat 'python -m venv venv'
                    bat '.\\venv\\Scripts\\activate'
                    
                    // Manually install pip in the virtual environment
                    bat 'python -m ensurepip --default-pip'
                    
                    // Upgrade pip to the latest version
                    bat '.\\venv\\Scripts\\python -m pip install --upgrade pip'
                }
            }
        }


        stage('Install Dependencies') {
            steps {
                script {
                    // Install dependencies from requirements.txt
                    bat 'pip install -r requirements.txt'
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    // Run the tests
                    bat 'pytest test.py'
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

        always {
            script {
                // Deactivate the virtual environment
                bat 'deactivate'
            }
        }
    }
}
