pipeline {
    agent any

    stages {
        stage('Build app') {
            steps {
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/NinadTippat/jenkinsPipeline.git']])
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    bat 'docker build -t jenkinsdocker1 .'
                }
            }
        }

        stage('Rename Image Tag') {
            steps {
                script {
                    bat 'docker tag jenkinsdocker1 ninadtippat/jenkinsdockerapp:image1'
                }
            }
        }

        stage('Push Image to Docker Hub') {
            steps {
                script {
                    bat 'docker login -u ninadtippat -p Ninad@2003'
                    bat 'docker push ninadtippat/jenkinsdockerapp:image1'
                }
            }
        }
    }
}
