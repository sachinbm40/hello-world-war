pipeline {
	agent any
    stages {
       stage('build') {
            steps {	
	sh 'mvn clean package'	
              }
        }
	 stage('copy') {
            steps {	
	sh 'cp /var/lib/jenkins/workspace/hello/target/hello-world-war-1.0.0.war /opt/apache-tomcat-9.0.56/webapps'	
              }
        }    
    }
}