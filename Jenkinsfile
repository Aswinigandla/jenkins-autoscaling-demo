
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Validate Application') {
            steps {
                bat '''
                    if not exist index.html exit /b 1
                    findstr /C:"Jenkins Auto Scaling Application" index.html >nul
                    if errorlevel 1 exit /b 1
                    echo Application validation successful
                '''
            }
        }
    }

    post {
        success {
            echo 'Build completed successfully!'
        }
        failure {
            echo 'Build failed. Check Console Output.'
        }
    }
}
