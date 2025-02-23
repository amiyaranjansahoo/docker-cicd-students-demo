pipeline{
	agent any
	tools {
		maven 'maven3'
	}

	stages{
		stage('Clone the code from Git'){
			steps{
				echo "Done from Jenkins"
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
				sh "docker build . -t amiyaranjansahoo/myimg:${BUILD_NUMBER}"
			}
		}
		
		stage('Login and pushed to Docker hub'){
			steps{
				withCredentials([string(credentialsId: 'docker_hub_pwd', variable: 'docker_password')]) {
					echo "Login and pushed to Docker hub"
					sh "docker login -u amiyaranjansahoo -p ${docker_password}"
					sh "docker push amiyaranjansahoo/myimg:${BUILD_NUMBER}"
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
