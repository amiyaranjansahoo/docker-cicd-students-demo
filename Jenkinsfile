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
                sh "docker build . -t saikiran64264/javahomeimg:${BUILD_NUMBER}"
            }
        }

        stage('Push the image to the docker registry') {
            steps {
                withCredentials([string(credentialsId: 'docker_pwd', variable: 'dockerpassword')]) {
                    echo 'Push the image to the docker registry'
                    sh "docker login -u saikiran64264 -p ${dockerpassword}"
                    sh "docker push saikiran64264/javahomeimg:${BUILD_NUMBER}"
                }
            }
        }

        stage('Create the container') {
            steps {
                echo 'Create the container'
                sh "docker rm -f mycontainer || true"
                sh "docker run -d -p 9090:8080 --name mycontainer saikiran64264/javahomeimg:${BUILD_NUMBER}"
            }
        }
    }
}
