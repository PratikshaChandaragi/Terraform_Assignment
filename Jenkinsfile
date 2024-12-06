pipeline {
    agent any

    environment {
        AWS_ACCESS_KEY_ID = credentials('aws-credentials')
        AWS_SECRET_ACCESS_KEY = credentials('aws-credentials')
    }

    stages {
        stage('Clone Repository') {
            steps {
                git branch:'main', url:'https://github.com/PratikshaChandaragi/Terraform_Assignment.git' // Replace with your repo
            }
        }

        stage('Terraform Init') {
            steps {
                sh "terraform init"
            }
        }

        stage('Terraform Plan') {
            steps {
                sh "terraform plan -out=tfplan"
            }
        }

        stage('Terraform Apply') {
            steps {
                sh "terraform apply -auto-approve tfplan"
            }
        }
    }

    post {
        always {
            echo 'Pipeline execution completed!'
        }
    }
}