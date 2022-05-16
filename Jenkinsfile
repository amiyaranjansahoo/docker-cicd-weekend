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
    }
}
