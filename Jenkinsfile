pipeline {
    agent any
    environment {
        PATH = "$PATH:/opt/homebrew/bin"
    }
    stages {
        stage("Checkout") {
            steps {
                checkout scm
            }
        }
        stage('Test') {
            steps {
                // Install npm packages
                sh '/opt/homebrew/bin/npm install'

                // Run tests
                sh 'npm test'
            }
        }
        stage("Build") {
            steps {
                sh 'npm run build'
            }
        }
        stage("Build Image"){
            steps{
                sh 'docker build -t my-node-app:1.0 .'
            }
        }
    }
}
