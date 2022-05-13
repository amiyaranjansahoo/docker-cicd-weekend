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
                sshagent(['tomcat']) {
                                  sh 'scp -o StrictHostKeyChecking=no target/myweb.war ec2-user@172.31.44.74:/software/tomcat9/webapps/'
                                 sh 'ssh ec2-user@172.31.44.74 /software/tomcat9/bin/shutdown.sh'
                                  sh 'ssh ec2-user@172.31.44.74 /software/tomcat9/bin/startup.sh'
                }
            }
        }
    }
}
