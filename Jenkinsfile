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
                sh "docker build . -t saikiran64264/javahomeimg1:${BUILD_NUMBER}"
            }
        }

        stage('Push the image to the docker registry') {
            steps {
               withCredentials([usernamePassword(credentialsId: 'docker_pwd', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
                   sh '''
                       echo $DOCKER_PASSWORD | docker login -u $DOCKER_USERNAME --password-stdin
                       docker push saikiran64264/javahomeimg1:${BUILD_NUMBER}
                   '''
               }
            }
        }

        stage('Create the container') {
            steps {
                echo 'Create the container'
                sh "docker rm -f mycontainer || true"
                sh "docker run -d -p 9090:8080 --name mycontainer saikiran64264/javahomeimg1:${BUILD_NUMBER}"
            }
        }
    }
}
