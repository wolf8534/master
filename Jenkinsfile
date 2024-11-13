pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
               git branch: 'main', url: 'https://github.com/wolf8534/master.git' // URL الخاص بالمستودع
               git branch: 'ahmed', url: 'https://github.com/wolf8534/master.git' // URL الخاص بالمستودع
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    // بناء صورة Docker باستخدام Dockerfile
                    sh 'docker build . -f Dockerfile -t docker.io/ahmedmaher07/doc:v0'
                    //run scripts
                    sh 'chmod +x HELLO.sh
                    sh './HELLO.sh'
                }
            }
        }
        stage('Push Docker Image') {
            steps {
                script {
                    // استخدام بيانات الاعتماد لتسجيل الدخول ودفع الصورة
                    withCredentials([usernamePassword(credentialsId: 'Dockerhub', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
                        sh 'docker login docker.io -u $DOCKER_USERNAME -p $DOCKER_PASSWORD'
                        sh 'docker push docker.io/ahmedmaher07/doc:v0'
                    }
                }
            }
        }
    }
}
