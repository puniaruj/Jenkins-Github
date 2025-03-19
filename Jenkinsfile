pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the application...'
            }
        }

        stage('Unit & Integration Tests') {
            steps {
                echo 'Running unit and integration tests...'
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Running code analysis...'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Performing security scan...'
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying application to Staging...'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on Staging...'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying application to Production...'
            }
        }
    }

    post {
        always {
            echo 'Pipeline Execution Completed'
        }
    }
}
