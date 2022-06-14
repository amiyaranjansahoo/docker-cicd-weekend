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
				echo "Code for Push the image to docker hub"
			}
		}
		
		stage('Deploy the image to dev server') {
			steps {
				echo "Code for Deploy the image to dev server"
			}
		}
	}
}
