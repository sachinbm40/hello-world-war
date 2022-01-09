pipeline {
	agent none
	stages {
	    
       stage('checkout') {
	       agent { label 'slave' }
            steps {
                sh 'sudo rm -rf hello-world-war'
	sh 'git clone https://github.com/sachinbm40/hello-world-war.git'	
              }
        }
	 stage('build') {
		 agent { label 'slave' }
	
            steps {
                dir('hello-world-war'){
                  sh 'pwd'
                sh 'ls'
            
                sh 'docker build -t tomcat:1.1 .'  
			
                }
	    }
	 }
                stage('push') {
			agent { label 'slave' }
	
            steps {
		    sh 'ls'
            sh 'docker tag tomcat:1.1 sachinbm40/myrepo:1.0'
		    sh 'docker images'
                sh 'docker push sachinbm40/myrepo:1.0'
         }
	 }
		 stage('deploy'){
		 agent { label 'jenkins' }
	     steps{
	        sh 'docker rm -f mytomcat'
	         sh 'docker run -d --name mytomcat -p 7777:8080 sachinbm40/myrepo:1.0'
	     }
	 }
	
    }
}
