pipeline {
    agent any

    parameters {
        choice(
            name: 'ENV',
            choices: ['dev', 'qa', 'prod'],
            description: 'Select environment'
        )
    }

    stages {
        stage('Selected Env') {
            steps {
                echo "Deploying to ${params.ENV}"
            }
        }
    }
}
