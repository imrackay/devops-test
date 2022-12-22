pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                bat 'docker build -t mynginx:latest -f Dockerfile .'
            }
        }
        stage('Deploy') {
            steps {
                withCredentials([string(credentialsId: 'DOCKER_REGISTRY_USERNAME', variable: 'USERNAME'),
                                 string(credentialsId: 'DOCKER_REGISTRY_PASSWORD', variable: 'PASSWORD')]) {
                    bat 'echo $USERNAME:$PASSWORD | docker login -u $USERNAME --password-stdin'
                bat 'docker tag mynginx:latest imrackay/test:latest'
                bat 'docker push imrackay/test:latest'
            }
        }
    }
}
