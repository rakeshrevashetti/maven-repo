pipeline {
    // add your slave label name
    agent { label 'agent-1'}
    tools{
        maven 'maven'
    }
    stages {
        stage ('Checkout_SCM') {

            steps {
          	    
	     checkout scm
            }
        }

        stage ('Maven_Build') {

            steps {
               sh 'mvn clean package'
            }
        }
        
        stage ('Deploy_Tomcat') {

            steps {
	      sshagent(['Tomcat_server']) {
              sh "scp -o StrictHostKeyChecking=no  target/maven-web-application.war  ec2-user@13.201.81.190:/opt/Apache_Tomcat9/webapps"
	      }
         }
        }
        
    }
}
