pipeline {
    agent any

    stages {
        stage('docker-build') {
            steps {
                echo 'building docker image....'
                dir('kube-backend') {
                    script {
                        imgback = docker.build("jenkins-pipeline-backend")
                    }
                }
            }
        }
        stage('docker-push') {
            steps {
                echo 'Push to dockerhub..'
                script {
                    docker.withRegistry('', 'shahed-dockerhub-cred') {
                        imgback.push()
                    }
                }
            }
        }
    }
}
