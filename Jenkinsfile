pipeline {
    agent any

    environment {
        AWS_REGION = "us-east-1"
        ECR_REPO = "269336772098.dkr.ecr.us-east-1.amazonaws.com/testpocjen01"
        IMAGE_TAG = "${BUILD_NUMBER}"
        CLUSTER_NAME = "srv6-va"
    }

    stages {

        stage('Build & Push') {
            steps {
                sh '''
                  docker build -t jenkins-demo:$IMAGE_TAG .
                  aws ecr get-login-password --region $AWS_REGION \
                  | docker login --username AWS --password-stdin $ECR_REPO
                  docker tag jenkins-demo:$IMAGE_TAG $ECR_REPO:$IMAGE_TAG
                  docker push $ECR_REPO:$IMAGE_TAG
                '''
            }
        }

        stage('Deploy to EKS') {
            steps {
                sh '''
                  aws eks update-kubeconfig --region $AWS_REGION --name $CLUSTER_NAME
                  sed -i "s|<ECR-URI>:v1|$ECR_REPO:$IMAGE_TAG|" deployment.yaml
                  kubectl apply -f deployment.yaml
                  kubectl apply -f service.yaml
                '''
            }
        }
    }
}
