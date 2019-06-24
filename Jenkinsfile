def label = "worker-agile-demo-frontend"

podTemplate(name: label, label: label,
        containers: [
                containerTemplate(name: 'docker', image: 'docker', command: 'cat', ttyEnabled: true),
                containerTemplate(name: 'kubectl', image: 'lachlanevenson/k8s-kubectl:v1.8.8', command: 'cat', ttyEnabled: true),
        ],
        volumes: [
                hostPathVolume(mountPath: '/var/run/docker.sock', hostPath: '/var/run/docker.sock')
        ]) {
    node(label) {

        def registry = "jinnerbichler/agile-demo-frontend"
        def registryCredential = "dockerhub"

        def myRepo = checkout scm
        def gitCommit = myRepo.GIT_COMMIT
        def gitBranch = myRepo.GIT_BRANCH
        def shortGitCommit = "${gitCommit[0..10]}"
        def previousGitCommit = sh(script: "git rev-parse ${gitCommit}~", returnStdout: true)

        stage('Test') {
            container('docker') {
                sh "docker --version"

                def dockerImage = docker.build("${registry}:${env.BUILD_ID}")
                docker.withRegistry('https://index.docker.io/v1/', registryCredential) {
                    dockerImage.push()
                }
            }
        }
    }
}