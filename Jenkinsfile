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
		
		stage('Download the image and create the container'){
			steps{
				echo "Download the image and create the container"
			}
		}
	}
}



