pipeline {
    agent any

    environment{
        IMAGE_NAME = "flast"
    }

    stages {

        stage('Checlout Code') {
            steps {
                echo "Pulling code from github"
                git branch: 'main' , url: 'https://github.com/jubairthematics/CICD-Project.git'
            }
        }

        stage('Build DOcker Image') {
            steps {
                script{
                    dockerImage = docker.build("${IMAGE_NAME}:${BUILD_NUMBER}")
                }
            }
        }
        stage('Run Container') {
            steps {
                sh " docker run -d -p 5000:5000 ${IMAGE_NAME}:${BUILD_NUMBER}"
            }
        }
    }
}