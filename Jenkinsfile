pipeline {
    agent any

    stages {
        stage('docker-build') {
            steps {
                echo 'building docker image....'
                sh'''
                cd kube-backend
                '''
                script {
                    docker.build("jenkins-pipeline-backend")
                }
            }
        }
        stage('test') {
            steps {
                echo 'Testing the project...'
            }
        }
        stage('deploy') {
            steps {
                echo 'Deploying the project in EC2..'
            }
        }
    }
}
