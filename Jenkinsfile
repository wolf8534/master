pipeline {
    agent any
    stages {
      stage('Checkout') {
            steps {
                git branch: 'ahmed', url: 'https://github.com/wolf8534/master.git' 
            }
        }
      stage('build docker ') {
            steps {
                script {
                
                    sh 'docker build . -f Dockerfile -t docker.io/ahmedmaher07/docss'  // Make the script executable (if not already)
                    sh 'docker exec -it docker.io/ahmedmaher07/docss'          // Run the Hello World script
                }
            }
        }
    }
      stage('build docker ') {
            steps {
                script {
                
                    withCredentials([usernamePassword(credentialsId: 'Docker_hub', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
                        sh 'docker login docker.io -u $DOCKER_USERNAME -p $DOCKER_PASSWORD'
                        sh 'docker push docker.io/ahmedmaher07/doc:v0'
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
