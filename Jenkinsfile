pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    credentialsId: 'github_divakar-007_credentials',
                    url: 'https://github.com/divakar-007/flask-jenkins-project.git'
            }
        }

        stage('Create Virtual Environment') {
            steps {
                bat '"C:\\Users\\DIVAKAR\\AppData\\Local\\Programs\\Python\\Python39\\python.exe" -m venv venv'
            }
        }

        stage('Activate & Install Requirements') {
            steps {
                bat 'venv\\Scripts\\activate && pip install -r requirements.txt'
            }
        }

        stage('Run Flask App (Test Mode)') {
            steps {
                bat 'venv\\Scripts\\activate && python app.py'
            }
        }
    }

    post {
        success {
            echo '✅ Build Successful! Flask App Pipeline Completed.'
        }
        failure {
            echo '❌ Build Failed! Please check logs.'
        }
    }
}
