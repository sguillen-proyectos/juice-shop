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

        stage('run-security-tests') {
            steps {
                build job: 'test-job-sergio', wait: false
            }
        }
    }
}
