pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'docker build -t mynginx:latest -f Dockerfile .'
            }
        }
    }
}
