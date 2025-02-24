pipeline{
	agent any
	tools {
		maven 'maven3'
	}
	stages{
		stage('Clone the code from Git'){
			steps{
				echo "Its configured from Jenkins UI"
			}
		}
		
		stage('Build using maven'){
			steps{
				echo "Build using maven"
				sh 'mvn clean package'
			}
		}
		
		stage('Build the docker image'){
			steps{
				echo "Build the docker image"
				sh 'docker build . -t amiyaranjansahoo/dockerimg0700am:${BUILD_NUMBER}'
			}
		}
		
		stage('Login and pushed to Docker hub'){
			steps{
				withCredentials([string(credentialsId: 'dockerpwd', variable: 'dockerpassword')]) {
				echo "Login and pushed to Docker hub"
				sh "docker login -u amiyaranjansahoo -p ${dockerpassword}"
				sh "docker push amiyaranjansahoo/dockerimg0700am:${BUILD_NUMBER}"
				}
			}
		}
		
		stage('create the container in a remote server'){
			steps{
				echo "create the container in a remote server"
				sshagent(['dockerssh']) {
				sh "ssh -o StrictHostKeyChecking=no ec2-user@172.31.35.32 docker rm -f mycontainer"
				sh "ssh -o StrictHostKeyChecking=no ec2-user@172.31.35.32 docker run -d -p 8080:8080 --name mycontainer amiyaranjansahoo/dockerimg0700am:${BUILD_NUMBER}"
				}
			}
		}
	}
}
