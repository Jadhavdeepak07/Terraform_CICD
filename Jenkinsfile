
pipeline {
    agent any

    parameters {
        choice(
            name: 'Action',
            choices: ['apply', 'destroy'],
            description: 'Select Terraform action'
        )
    }

    stages {

        stage('Clone') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Jadhavdeepak07/Terraform_CICD.git'
            }
        }

        stage('Terraform Init') {
            steps {
                sh 'terraform init'
            }
        }

        stage('Terraform Validate') {
            steps {
                sh 'terraform validate'
            }
        }

        stage('Terraform Plan') {
            steps {
                sh 'terraform plan'
            }
        }

        stage('Terraform Apply/Destroy') {
            steps {
                sh "terraform ${params.Action} -auto-approve"
            }
        }
    }

    post {
        success {
            echo 'Terraform pipeline completed successfully!'
        }

        failure {
            echo 'Terraform pipeline failed!'
        }
    }
}
