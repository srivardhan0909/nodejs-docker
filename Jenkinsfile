pipeline{
    agent any
    stages{
        stage("checkout"){
            steps{
                checkout scm
            }
        }
        stage('Install npm packages') {
    environment {
        PATH = "$PATH:/opt/homebrew/bin"
    }
    steps {
        sh '/opt/homebrew/bin/npm install'
    }
}
        stage("Build"){
            steps{
                sh 'npm run build'
            }
        }
    }
}
