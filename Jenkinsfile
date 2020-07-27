properties([pipelineTriggers([githubPush()])])

pipeline {
    agent any

    stages {
        stage('docker-build') {
            steps {
                // sh 'docker build -t donkeysharp/juice-shop:latest .'
                sh 'echo "docker build -t donkeysharp/juice-shop:latest ."'
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
