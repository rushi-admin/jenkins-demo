pipeline {
    agent any

    environment {
        AWS_REGION = "us-east-1"
        ECR_REPO   = "269336772098.dkr.ecr.us-east-1.amazonaws.com/testpocjen01"
        IMAGE_TAG  = "v1"
        IMAGE_NAME = "jenkins-demo"
    }

    stages {

        stage('Build') {
            steps {
                sh """
                  docker build -t ${IMAGE_NAME}:${IMAGE_TAG} .
                """
            }
        }

        stage('ECR Login') {
            steps {
                sh """
                  aws ecr get-login-password --region ${AWS_REGION} \
                  | docker login --username AWS --password-stdin ${ECR_REPO}
                """
            }
        }

        stage('Push Image') {
            steps {
                sh """
                  docker tag ${IMAGE_NAME}:${IMAGE_TAG} ${ECR_REPO}:${IMAGE_TAG}
                  docker push ${ECR_REPO}:${IMAGE_TAG}
                """
            }
        }
    }
}
