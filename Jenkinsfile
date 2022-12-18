pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                docker build -t mynginx_1:latest -f Dockerfile
            }
        }
    }
}
