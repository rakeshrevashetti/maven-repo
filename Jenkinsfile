pipeline {
   
    agent { label 'Slave-Node'}
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
	      sshagent(['Tomcat']) {
              sh "scp -o StrictHostKeyChecking=no  target/maven-web-application.war  ec2-user@13.233.98.241:/opt/tomcat9/webapps"
	      }
         }
        }
        
    }
}
