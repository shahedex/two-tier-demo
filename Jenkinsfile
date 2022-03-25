pipeline {
    agent any

    stages {
        stage('docker-build') {
            steps {
                echo 'building docker image....'
                dir('kube-backend') {
                    script {
                        imgback = docker.build("shahedmehbub/jenkins-pipeline-backend")
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
        stage('docker-deploy') {
            steps {
              echo 'Deploying to EC2...'
                script {
                    withCredentials([string(credentialsId: 'docker-server-pass', variable: 'SSHPASS')]) {
                        sh'''
                              sshpass -e ssh -o StrictHostKeyChecking=no ubuntu@65.2.6.22 "docker stop cicd-test && docker rm cicd-test && docker rmi shahedmehbub/jenkins-pipeline-backend:latest && docker run -d --name cicd-test -p 5000:5000 shahedmehbub/jenkins-pipeline-backend:latest"
                        '''
                    }
                }
            }
        }
    }
}
