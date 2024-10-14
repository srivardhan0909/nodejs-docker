pipeline{
    agent any
    stages{
        stage("checkout"){
            steps{
                checkout scm
            }
        }
        stage("Test"){
            steps{
                sh "/opt/homebrew/bin/npm install"
            }
        }
        stage("Build"){
            steps{
                sh 'npm run build'
            }
        }
    }
}
