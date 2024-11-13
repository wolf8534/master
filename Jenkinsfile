pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/wolf8534/master.git'  // Replace with your repository URL
            }
        }
    }
   
        stage('Build Docker Image') {
            steps {
                script {
                    // بناء صورة Docker باستخدام Dockerfile
                    sh 'docker build build . -f Dockerfile -t docker.io/ahmedmaher07/doc:v0'
                    sh 'docker run -d -p 6000:6000 docker.io/ahmedmaher07/doc:v0'
                }
            }
        }
        stage('Push Docker Image') {
            steps {
                script {
                    // تسجيل الدخول إلى Docker Hub
                    sh 'docker login -u ahmedmaher07     -p Aa01120589983'
                    
                    // دفع الصورة إلى Docker Hub
                    sh 'docker push docker.io/ahmedmaher07/doc:v0'
                }
            }
        }
    }
