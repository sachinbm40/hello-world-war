pipeline {
	agent none
	stages {
	    
       stage('checkout') {
	       agent { label 'dj' }
            steps {
                sh 'sudo rm -rf hello-world-war'
	sh 'git clone https://github.com/Urssharath/hello-world-war.git'	
              }
        }
	 stage('build') {
		 agent { label 'dj' }
	
            steps {
                dir('hello-world-war'){
                  sh 'pwd'
                sh 'ls'
            
                sh 'docker build -t tomcat:ver1.1 .'  
                }
	    }
	 }
                stage('push') {
			agent { label 'dj' }
	
            steps {
            sh 'docker tag tomcat:ver1.1 sharath/pushdjf:1.0'
                sh 'docker push sharath/pushdjf:1.0'
         }
	 }
	 stage('deploy'){
		 agent { label 'dj02' }
	     steps{
	        sh 'docker rm -f mytomcat'
	         sh 'docker run -d --name mytomcat -p 7777:8080 sharath/pushdjf:1.0'
	     }
	 }
    }
}
