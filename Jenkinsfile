node {
    def app

    stage('Clone repository') {
        checkout scm

        docker.image('mysql:5').withRun('-e "MYSQL_ROOT_PASSWORD=my-secret-pw" -p 3306:3306') { c ->
            /* Wait until mysql service is up */
            sh 'while ! mysqladmin ping -h0.0.0.0 --silent; do sleep 1; done'
            /* Run some tests which require MySQL */
            sh 'make check'
        }
    }

    stage('Build image') {
        app = docker.build("getintodevops/hellonode")
    }

    stage('Test image') {
    }

    stage('Push image') {
    }
}