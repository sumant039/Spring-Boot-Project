
pipeline {
    agent any
    environment{
        BUILD_NUMBER = "${BUILD_NUMBER}"
    }
   
    stages {
        stage('Build MAven') {
            steps {
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/sumant039/Spring-Boot-Project']])
                sh 'mvn clean install'
            }
        }
        stage('Build docker image') {
            steps {
                script{
                    sh 'docker build -t sumant039/spring-boot-docker:${env.BUILD_NUMBER} .'
                }
            }
        }
        stage('Deploy images') {
            steps {
                script{
                    withCredentials([string(credentialsId: 'sumant039', variable: 'dockerhubpas')]) {
                    sh 'docker login -u sumant039 -p ${dockerhubpas}'
    // some block
}                   
                    sh 'docker push sumant039/spring-boot-docker:${env.BUILD_NUMBER}'
                }
            }
        }
    }
}
