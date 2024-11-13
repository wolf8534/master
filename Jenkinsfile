pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'ahmed', url: 'https://github.com/wolf8534/master.git' 
            }
        }
        stage('Build Docker Image') {
            steps {
                // run scripts
                sh 'chmod +x Dockerfile'
                sh './Dockerfile' 
            }
        }
    }
}
