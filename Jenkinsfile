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

    }
}