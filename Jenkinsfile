pipeline{
    agent{
        lable 'docker'
    }
}

stages{
    stage('build docker image'){
        steps{
            sh 'docker build -t tawfiq/docker-react -f Dockerfile.dev .'
        }
    }
}
stage('Run tests'){
    steps{
        env.DOCKERBUILDKIT = 'legacy'
        sh 'docker run -e CI=true tawfiq/docker-react npm test'
    }
}
