pipeline {
  agent any 

  stages {
    stage('Checkout') {
      steps {
                echo 'Cloning code'
                checkout scm
            }
    }
    stage('Build'){
      steps {
        echo 'building code'
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
  }
}
