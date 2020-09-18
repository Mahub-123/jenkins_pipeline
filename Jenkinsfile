	pipeline {
	agent none

	stages {
		
		//parallel {
			
		stage ('make') {
			agent { label 'slave1' }
			steps {
			  	git 'https://github.com/Mahub-123/github1.git'
					sh 'make'
				     sh 'sleep 10'
			       }
			}
			
		stage ('Java Project') {
			agent { label 'slave2' }
			steps {
				git 'https://github.com/Mahub-123/java_maven_web.git'
				sh 'mvn clean install'
			      }
			}
		//}
		
	}
}
