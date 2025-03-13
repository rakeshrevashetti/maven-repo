pipeline {
    agent { label 'slavenode1'}
    tools { maven 'maven1'}
    stages {
        stage('git-cloning') {
            steps {
                sh 'git clone url:'https://github.com/rakeshrevashetti/maven-repo.git' branch:'main''
            }
        }
        stage('build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage(deploy) {
            steps {
                sshagent([['tomcat']]) {
                    sh 'scp -o strictHostKeyChecking=no target/maven-web-application.war ec2-user@54.171.133.255:/opt/tomcat9/webapps'
                }
            }
        }    
    }
}
