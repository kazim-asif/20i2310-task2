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
                    if (isUnix()) {
                        sh 'python3 -m venv venv'
                        sh 'source venv/bin/activate'
                        sh 'python3 -m pip install --upgrade pip'
                    } else {
                        bat 'python -m venv venv'
                        bat '.\\venv\\Scripts\\activate'
                        bat 'python -m pip install --upgrade pip'
                    }
                }
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    // Install dependencies from requirements.txt
                    if (isUnix()) {
                        sh 'pip install -r requirements.txt'
                    } else {
                        bat 'pip install -r requirements.txt'
                    }
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    // Run the tests
                    if (isUnix()) {
                        sh 'pytest test.py'
                    } else {
                        bat 'pytest test.py'
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

        always {
            script {
                // Deactivate the virtual environment
                if (isUnix()) {
                    sh 'deactivate'
                } else {
                    bat 'deactivate'
                }
            }
        }
    }
}
