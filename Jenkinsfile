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
       stage('Docker Push') {
    steps {
        withCredentials([usernamePassword(credentialsId: 'nodejs-docker', passwordVariable: 'DOCKERHUB_PASSWORD', usernameVariable: 'DOCKERHUB_USERNAME')]) {
            // Debug: Print username and masked password
            sh 'echo Username: $DOCKERHUB_USERNAME'
            sh 'echo Password: $DOCKERHUB_PASSWORD'

            // Use --password-stdin for secure login
            sh 'echo $DOCKERHUB_PASSWORD | docker login -u $DOCKERHUB_USERNAME --password-stdin'

            // Tag and push Docker image
            sh 'docker tag my-node-app:1.0 srivardhan0909/nodejs-docker'
            sh 'docker push srivardhan0909/nodejs-docker'

            // Docker logout
            sh 'docker logout'
        }
    }
}

    }
}
