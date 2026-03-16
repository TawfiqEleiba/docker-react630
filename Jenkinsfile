pipeline {
    agent any // خليها any دلوقتي عشان يشتغل على الـ node الأساسية بسهولة

    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t tawfiq/docker-react -f Dockerfile.dev .'
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    env.DOCKER_BUILDKIT = '0' // القيمة الصحيحة لقفل الـ BuildKit لو محتاجه
                }
                sh 'docker run -e CI=true tawfiq/docker-react npm test'
            }
        }
    }
}
//this is for testing webhook 
