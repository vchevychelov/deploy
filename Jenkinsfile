pipeline {
    agent any
    stages {
        stage('Git checkout') {
           steps{
                git branch: 'main', credentialsId: 'Github', url: 'https://github.com/vchevychelov/deploy.git'
            }
        }
        stage('terraform Init') {
            steps{
                sh 'terraform init'
            }
        }
        stage('terraform apply') {
            steps{
                sh 'terraform apply --auto-approve'
            }
        }
        stage('Deploy') {
            steps {
                ansiblePlaybook playbook: 'playbook.yml', inventory: './inventory/hosts.ini'
            }
        }
    }
}