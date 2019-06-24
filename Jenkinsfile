pipeline {
    agent any

    def app

    stages {
        stage('Build') {
            steps {
                app = docker.build("jinnerbichler/agile-demo-frontend-service")
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}