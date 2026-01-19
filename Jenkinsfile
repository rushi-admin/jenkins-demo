pipeline {
    agent any

    environment {
        IMAGE_NAME = "jenkins-demo"
        IMAGE_TAG = "v1"
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Docker Build') {
            steps {
                sh '''
                  docker build -t $IMAGE_NAME:$IMAGE_TAG .
                '''
            }
        }

        stage('Docker Images') {
            steps {
                sh 'docker images'
            }
        }
    }
}
