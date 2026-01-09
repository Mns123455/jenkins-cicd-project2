pipeline {
    agent any

    environment {
        DEPLOY_DIR = "C:\\deploy\\jenkins-project2"
    }

    stages {

        stage('Checkout') {
            steps {
                echo 'Source code checked out'
            }
        }

        stage('Build') {
            steps {
                bat 'app.bat'
            }
        }

        stage('Test') {
            steps {
                bat 'test.bat'
            }
        }

        stage('Package') {
            steps {
                bat '''
                if not exist dist mkdir dist
                copy app.bat dist\\
                copy version.txt dist\\
                '''
            }
        }

        stage('Deploy') {
            steps {
                bat '''
                if not exist %DEPLOY_DIR% mkdir %DEPLOY_DIR%
                copy dist\\* %DEPLOY_DIR%\\
                '''
            }
        }
    }
}
