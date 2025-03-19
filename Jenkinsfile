pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the application...'
                sh 'mvn clean package'  // For Java, change as per your project
            }
        }

        stage('Unit & Integration Tests') {
            steps {
                echo 'Running unit and integration tests...'
                sh 'mvn test'
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Running code analysis...'
                sh 'sonar-scanner -Dsonar.projectKey=my-project'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Performing security scan...'
                sh 'dependency-check.sh --project my-project'
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying application to Staging...'
                sh 'scp target/my-app.jar ubuntu@staging-server:/home/ubuntu/'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on Staging...'
                sh 'curl -f http://staging-server:8080/health'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying application to Production...'
                sh 'scp target/my-app.jar ubuntu@prod-server:/home/ubuntu/'
            }
        }
    }

    post {
        always {
            echo 'Pipeline Execution Completed'
        }
        failure {
            mail to: 'your-email@example.com',
                subject: "Jenkins Pipeline Failed",
                body: "Pipeline failed at stage: ${env.STAGE_NAME}"
        }
        success {
            mail to: 'your-email@example.com',
                subject: "Jenkins Pipeline Successful",
                body: "Pipeline completed successfully!"
        }
    }
}