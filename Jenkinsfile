pipeline {
    agent {label 'node'}
    triggers { pollSCM('* * * * *') }
    stages {
        stage('git') {
            steps {
                git branch: 'canary', url: 'https://github.com/gopivurata/react-storefront.git'
            }
        }
        stage('docker') {
            steps {
                sh '''docker info
                  docker image build -t gopivurata/react-storefront:DEV .
                  docker image push gopivurata/react-storefront:DEV'''
            }
        }
    }
}