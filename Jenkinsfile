pipeline {
    agent any

    stages {
        stage('build') {
           steps {
               echo 'Building docker image..'
               sh'''
               cd kube-backend
               docker build -t pipeline-backend .
               docker images
               '''
            }
        }
         stage('Test') {
            steps {
                echo 'Test'
            }
        }
         stage('Deploy') {
            steps {
                echo 'Deploy'
            }
        }
    }
}

