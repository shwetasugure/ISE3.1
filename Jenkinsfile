pipeline {
    agent any
    environment {
        DOCKER_CREDENTIALS = credentials('dockerhub-creds')
        IMAGE_NAME = "shweta33/target/SimpleJavaApp-1.0-SNAPSHOT"
    }
    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/shwetasugure/ISE3.1.git'
            }
        }
        stage('Build Java Application') {
            steps {
                sh 'mvn clean package -DskipTests' // Adjust as necessary
            }
        }
        stage('Build Docker Image') {
            steps {
                sh "docker build -t ${IMAGE_NAME}:latest ."
            }
        }
        stage('Push to Docker Hub') {
            steps {
                sh "echo ${DOCKER_CREDENTIALS_PSW} | docker login -u ${DOCKER_CREDENTIALS_USR} --password-stdin"
                sh "docker push ${IMAGE_NAME}:latest"
            }
        }
    }
    post {
        always {
            sh "docker logout"
        }
    }
}
