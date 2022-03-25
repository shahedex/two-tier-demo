pipeline {
    agent any

    stages {
        stage('build') {
            steps {
                echo 'building docker image....'
                sh'''
                docker build -t pipeline-backend .
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
