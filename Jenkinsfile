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
        stage('Install npm packages') {
            steps {
                sh '/opt/homebrew/bin/npm install'
            }
        }
        stage("Build") {
            steps {
                sh 'npm run build'
            }
        }
    }
}
