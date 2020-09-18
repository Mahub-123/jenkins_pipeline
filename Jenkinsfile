pipeline {
	agent none	
	stages {
	stage('Build c') {
		agent { label 'slave1' }
		steps {
		      echo 'Building c-project'
			sh '''								
							if [[ -d "github1" ]]; then
								cd github1 && git pull 
								make
							else
							git clone  https://github.com/Mahub-123/github1.git
								cd github1
								make
							fi					
			   '''
		}
	}
	stage('Build JAVA'){
		agent { label 'slave2' }
		steps {
		     echo 'Building JAVA project...'
			sh '''
							if [[ -d "java_maven_web" ]]; then
								cd java_maven_web && git pull 
								mvn clean install
								echo "Build Successful"
								cd target
								cp java-tomcat-maven-example.war /home/ec2-user/deploying_part
								echo "Deployed Successful"
							else
							git clone  https://github.com/Mahub-123/java_maven_web.git
								cd java-maven_web
								mvn clean install
								echo "Build Successful...!!!"
								cd target
								cp java-tomcat-maven-example.war /home/ec2-user/deploying_part
								echo "Deployed Successful"
							fi
				'''
		}
	}

}

}
