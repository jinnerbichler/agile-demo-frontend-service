node {
    def app

    stage('Clone repository') {
        checkout scm
    }

    stage('Build image') {
        app = docker.build("getintodevops/hellonode")
    }

    stage('Test image') {
    }

    stage('Push image') {
    }
}