
pipeline {
	agent any
	
	stages {
		stage('Build the project') {
			steps {
				sh 'mvn clean package'
			}
		}
		
		stage('Create the docker image') {
			steps {
				echo "code here Create the docker image"
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
