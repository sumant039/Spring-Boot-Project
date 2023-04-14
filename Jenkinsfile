pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Deploy') {
            environment {
                APP_NAME = 'my-spring-boot-app'
            }
            steps {
                script {
                    docker.build("$APP_NAME:${env.BUILD_NUMBER}")
                    docker.withRegistry('https://hub.docker.com', 'docker-credentials') {
                        docker.image("$APP_NAME:${env.BUILD_NUMBER}").push()
                    }
            }
        }
    }
}