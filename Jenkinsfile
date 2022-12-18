pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'docker build -t mynginx_1:latest -f Dockerfile .'
            }
        }
    }
}
