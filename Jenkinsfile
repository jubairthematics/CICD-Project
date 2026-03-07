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

        stage ('Build Docker Image') {
            steps{
                script{
                    echo "Building Image"
                    dockerimage = docker.build("${IMAGE_NAME}:${BUILD_NUMBER}")
                }
            }
        }

        stage ('Run Docker Container') {
            steps {
                script{
                    echo "Running Container"
                    sh "docker rm -f ${IMAGE_NAME} || true"
                    sh "docker run -d -p 80:80 --name ${IMAGE_NAME} ${IMAGE_NAME}:${BUILD_NUMBER}"
                }
            }
        }
    }
    
    post {
        always {
            echo " pipeline finished for build #${BUILD_NUMBER}"
            }
        success {
            echo "Build seceeded! Application should be rrrunning at http://localhost:80"
        }
        failure {
            echo "Build failed! Please check the logs for more details."
        }

    }
}