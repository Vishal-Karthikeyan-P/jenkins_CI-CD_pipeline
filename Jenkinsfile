pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out source code...'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building Python application...'
                bat '"C:\\Users\\25mx130\\AppData\\Local\\Microsoft\\WindowsApps\\python.exe" --version'
                bat '"C:\\Users\\25mx130\\AppData\\Local\\Microsoft\\WindowsApps\\python.exe" -m py_compile app.py'
            }
        }

        stage('Test') {
            steps {
                echo 'Running unit tests...'
                bat '"C:\\Users\\25mx130\\AppData\\Local\\Microsoft\\WindowsApps\\python.exe" -m unittest test_app.py'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'
                bat 'if not exist deploy mkdir deploy'
                bat 'copy /Y app.py deploy\\app.py'
            }
        }
    }

    post {
        success {
            echo 'CI/CD Pipeline completed successfully!'
        }

        failure {
            echo 'CI/CD Pipeline failed!'
        }
    }
}
