pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                bat 'docker build -t mynginx:latest -f Dockerfile .'
            }
        }
    }
}
