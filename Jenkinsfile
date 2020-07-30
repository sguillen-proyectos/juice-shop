properties([pipelineTriggers([githubPush()])])

pipeline {
    agent any

    options {
        timestamps ()
    }

    stages {
        stage('docker-build') {
            steps {
                sh 'echo Hola mundo'
                sh 'docker build -t donkeysharp/juice-shop:latest .'
                sh 'docker push donkeysharp/juice-shop:latest'
            }
        }

        stage('deploy-application') {
            steps {
                build job: 'deploy-juice-shop', wait: true
            }
        }

        stage('run-security-tests') {
            steps {
                build job: 'test-job-sergio', wait: false
            }
        }
    }
}
