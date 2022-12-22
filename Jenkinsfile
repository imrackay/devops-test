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
                bat 'docker login -u $DOCKER_HUB_USERNAME -p $DOCKER_HUB_PASSWORD'
                bat 'docker tag mynginx:latest imrackay/test:latest'
                bat 'docker push imrackay/test:latest'
            }
        }
    }
}
