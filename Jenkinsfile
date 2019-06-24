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
        def dockerImage

        /***************** Clone project ******************************/
//        stage('Clone') {
//            checkout scm
//        }
//
//        /***************** BUILD Docker image ******************************/
//        stage('Build') {
//            container('docker') {
//                dockerImage = docker.build("${registry}:${env.BUILD_ID}", "--no-cache .")
//            }
//        }
//
//        /***************** PUSH Docker image ******************************/
//        if (env.BRANCH_NAME == 'master') {
//            stage('Push') {
//                container('docker') {
//                    docker.withRegistry('https://index.docker.io/v1/', registryCredential) {
//                        dockerImage.push("master")
//                        dockerImage.push("latest")
//                    }
//                }
//            }
//        }
//        if (env.BRANCH_NAME == 'staging') {
//            stage('Push') {
//                container('docker') {
//                    docker.withRegistry('https://index.docker.io/v1/', registryCredential) {
//                        dockerImage.push("staging")
//                    }
//                }
//            }
//        }

        /***************** Deploy application ******************************/
        if (env.BRANCH_NAME == 'master') {
            stage('Deploy') {
                sh "kubectl get pods"
            }
        }
    }
}