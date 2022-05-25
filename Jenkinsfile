@Library('sharedlib')_
pipeline {
    agent any
    tools {
        maven 'maven3'
    }
    stages {
        //stage('Clone the project from git') {
            //steps {
                //git credentialsId: 'git_cred', url: 'https://github.com/amiyaranjansahoo/devops-mvn.git'
            //}
        //}
        
        stage('Build it using Maven') {
            steps {
                sh 'mvn clean package'
            }
        }
        
        stage('Transfer the artifact and deploy') {
            steps {
                deployTomcat('tomcat','ec2-user','172.31.37.225')
            }
        }
		
		stage('Upload to nexus') {
            steps {
                nexusArtifactUploader artifacts: [[artifactId: 'myweb', classifier: '', 
				file: 'target/myweb.war', type: 'war']], 
				credentialsId: 'amiya', 
				groupId: 'in.javahome', 
				nexusUrl: '172.31.33.15:8081', 
				nexusVersion: 'nexus3', 
				protocol: 'http', 
				repository: 'sample-release', 
				version: '0.0.2-SNAPSHOT'
            }
        }
    }
}
