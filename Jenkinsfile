pipeline {
    agent {
        docker { image 'benhall/dind-jenkins-agent' }
    }
    stages {
        stage('Test') {
            steps {
                sh 'docker --version'
            }
        }
    }
}