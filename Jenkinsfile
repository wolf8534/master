pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'ahmed', url: 'https://github.com/wolf8534/master.git' 
            }
        }
        stage('Run Hello World') {
            steps {
                script {
                
                    sh 'chmod +x h.py'  // Make the script executable (if not already)
                    sh './h.py'          // Run the Hello World script
                }
            }
        }
    }
    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
