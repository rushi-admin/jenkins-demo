pipeline {
  agent any

  environment {
    APP_NAME = 'jenkins-demo-app'
    ENV = 'dev'
    AWS_REGION = 'us-east-1'
  }

  stages {
    stage('Checkout') {
      steps {
                echo 'Cloning code'
                checkout scm
            }
    }
    stage('Build'){
      steps {
        echo 'building app ${APP_NAME}'
      }
    }
    stage('Test'){
      steps {
        echo 'testing the code'
      }
    }
    stage('Deploy'){
      steps {
        echo 'deploying the code....deployed!'
      }
    }
    stage('Print Env'){
      echo 'app name is ${APP_NAME}, env is ${ENV} and region is ${AWS_REGION}'
    }
  }
}
