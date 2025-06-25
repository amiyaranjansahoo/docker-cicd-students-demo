pipeline {
    agent any

    tools {
        maven 'mvn3'
    }

    stages {
        stage('Clone the sourcecode') {
            steps {
                echo 'Already configured'
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
                // Example: sh 'docker push saikiran64264/myimg2:v3'
            }
        }

        stage('Create the container') {
            steps {
                echo 'Create the container'
                // Example: sh 'docker run -d --name mycontainer saikiran64264/myimg2:v3'
            }
        }
    }
}
