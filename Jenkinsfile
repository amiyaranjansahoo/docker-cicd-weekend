pipeline {
	agent any
	tools {
	  maven 'maven3'
	}
	
	stages {
		stage('Build the project using maven') {
			steps {
				sh 'mvn clean package'
			}
		}
		
		stage('Create the docker image') {
			steps {
				sh "docker build . -t amiyaranjansahoo/docker-img-weekend"
			}
		}
		
		stage('Push the image to docker hub') {
			steps {
				withCredentials([string(credentialsId: 'docker-hub', variable: 'dockerPWD')]) {
				docker login -u amiyaranjansahoo -p ${dockerPWD}
				docker push amiyaranjansahoo/docker-img-weekend
				}
			}
		}
		
		stage('Deploy the image to dev server') {
			steps {
				echo "Code for Deploy the image to dev server"
			}
		}
	}
}
