pipeline {
    agent any

    environment {
        DOCKER_HUB_USERNAME = credentials('dockertest')
        DOCKER_HUB_PASSWORD = credentials('dockertest')
    }
    stages {
        stage('Build') {
            steps {
                bat 'docker build -t mynginx:latest -f Dockerfile .'
            }
        }
        stage('Deploy') {
            steps {
                withCredentials([string(credentialsId: 'dockertest', variable: 'DOCKER_HUB_CREDS')]) {
                    bat 'echo "$DOCKER_HUB_CREDS" | docker login -u $DOCKER_HUB_USERNAME --password-stdin'
                }
                bat 'docker tag mynginx:latest imrackay/test:latest'
                bat 'docker push imrackay/test:latest'
            }
        }
    }
}
