pipeline {
    agent any

    environment {
        APP_NAME = "jenkins-demo-app"
        ENV = "dev"
        AWS_REGION = "ap-south-1"
    }

    stages {
        stage('Print Env') {
            steps {
                echo "App name is ${APP_NAME}"
                echo "Environment is ${ENV}"
                echo "Region is ${AWS_REGION}"
            }
        }

        stage('Build') {
            steps {
                echo "Building ${APP_NAME}"
            }
        }
    }
}
