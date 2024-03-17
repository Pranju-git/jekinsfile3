pipeline {
	agent any 

parameters {
		choice(name: 'ENVIRONMENT', choices: ['QA','UAT'], description: 'Pick Environment value')
	}

	
	stages {
	    stage('Checkout') {
	        steps {
			checkout scm			       
		      }}
		stage('Build') {
	           steps {
			  sh '/home/pranjali/Documents/Devops-software/apache-maven-3.9.6/bin/mvn install'
	                 }}
		stage('Deployment'){
		    steps {
			script {
			 if ( env.ENVIRONMENT == 'QA' ){
        	sh 'sshpass -p "admin" scp target/jenkinsfile3.war admin@172.17.0.2:/home/admin/appfiles/apache-tomcat-9.0.85/webapps'
        	echo "deployment has been done on QA!"
			 }
			else if ( env.ENVIRONMENT == 'UAT' ){
    		sh 'sshpass -p "admin" scp target/jenkinsfile3.war admin@172.17.0.3:/home/admin/appfiles/apache-tomcat-9.0.85/webapps '
    		echo "deployment has been done on UAT!"
			}
			echo "deployment has been done!"
			
			
			}}}	

}}
