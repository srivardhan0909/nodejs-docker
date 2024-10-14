pipeline {
    agent any
    environment {
        PATH = "$PATH:/usr/local/bin:/opt/homebrew/bin"  
    }
    stages {
        stage("Checkout") {
            steps {
                checkout scm
            }
        }
        stage('Install npm packages') {
            steps {
                // Install npm packages
                sh '/opt/homebrew/bin/npm install'

                // Run tests
                sh 'npm test'
            }
        }
        stage("Build") {
            steps {
                // Run build command
                sh 'npm run build'
            }
        }
        stage('Docker Build') {
            steps {
                // Build Docker image
                sh 'docker build -t my-node-app:1.0 .'
            }
        }
    }
}
