pipeline {
    agent any
    tools {
        maven 'Maven_3.8.7'
    }
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Ranjanp864/1bi22cs126.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'target/*.war', fingerprint: true
            }
        }
         stage('Deploy') {
            steps {
                sh 'mvn clean package'
                ansiblePlaybook playbook: 'ansible/deploy.yml', inventory: 'ansible/hosts.ini'
            }
        }
    }
}

