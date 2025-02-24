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
				sh 'docker build . -t amiyaranjansahoo/dockerimg0700am:v1'
			}
		}
		
		stage('Login and pushed to Docker hub'){
			steps{
				echo "Login and pushed to Docker hub"
			}
		}
		
		stage('Download the image and create the container'){
			steps{
				echo "Download the image and create the container"
			}
		}
	}
}
