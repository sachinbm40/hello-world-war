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
		    sh 'ls'
            sh 'docker tag tomcat:ver1.1 urssharath/myrepo:1.0'
		    sh 'docker images'
                sh 'docker push urssharath/myrepo:1.0'
         }
	 }
	
    }
}
