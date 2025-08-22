pipeline {
    agent any

    tools {
        maven 'mvn3'
    }

    stages {
        stage('Clone the sourcecode') {
            steps {
                echo 'Cloning the repository'
                git url: 'https://github.com/Saikiran650/docker-cicd-students-demo.git', branch: 'main'
            }
        }

        stage('Build the sourcecode using maven') {
            steps {
                echo 'Build the sourcecode using maven'
                sh 'mvn clean package'
            }
        }

        stage('Create the image') {
            steps {
                echo 'Create the image'
                sh 'docker build -t saikiran64264/myimg2:v3 .'
            }
        }

        stage('Push the image to the docker registry') {
            steps {
                echo 'Push the image to the docker registry'
                // Uncomment this if credentials and Docker login are set up
                // sh 'docker push saikiran64264/myimg2:v3'
            }
        }

        stage('Create the container') {
            steps {
                echo 'Create the container'
                // Uncomment and customize this if you want to run the container
                // sh 'docker run -d --name mycontainer saikiran64264/myimg2:v3'
            }
        }
    }
} 

