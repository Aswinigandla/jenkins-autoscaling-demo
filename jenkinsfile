
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
                sh '''
                    test -s index.html
                    grep -q "Jenkins Auto Scaling Application" index.html
                    echo "Application validation successful"
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
