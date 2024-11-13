pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'ahmed', url: 'https://github.com/wolf8534/master.git' 
            }
        }
        stage('runscript ') {
            steps {
                sh 'ls -l'
                // run scripts
                sh 'chmod +x script'
                sh './script' 
            }
        }
    }
}
