pipeline {
    agent any

    stages {
        stage('build') {
            steps {
                echo 'building docker image....'
                sh'''
                cd kube-backend
                docker build -t pipeline-backend .
                docker images
                '''
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
