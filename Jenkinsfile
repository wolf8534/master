pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/wolf8534/master.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    // بناء صورة Docker باستخدام Dockerfile
                    sh 'docker build . -f Dockerfile -t docker.io/ahmedmaher07/doc:v0'
                    sh 'docker run -d -p 6000:6000 docker.io/ahmedmaher07/doc:v0'
                }
            }
        }
        stage('Push Docker Image') {
            steps {
                script {
                    // تسجيل الدخول إلى Docker Hub
                       withCredentials([usernamePassword(credentialsId: 'Dockerhub', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
                        sh 'docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD'
                    // دفع الصورة إلى Docker Hub
                    sh 'docker push docker.io/ahmedmaher07/doc:v0'
                }
            }
        }
    }
}