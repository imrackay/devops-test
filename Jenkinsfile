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
                withCredentials([string(credentialsId: '3912d02a-72bd-41a7-ab24-a5b68a767960', variable: 'USERNAME'),
                                 string(credentialsId: '3912d02a-72bd-41a7-ab24-a5b68a767960', variable: 'PASSWORD')]) {
                    bat 'echo $USERNAME:$PASSWORD | docker login -u $USERNAME --password-stdin'
                bat 'docker tag mynginx:latest imrackay/test:latest'
                bat 'docker push imrackay/test:latest'
                }
            }
        }
    }
}
