pipeline {
  agent any
	
  tools {
	jdk 'jdk1.8'
	maven 'maven3'
  }
  
  stages {
    stage('Deploy CloudHub') { 
      environment { 
	        ANYPOINT_CREDENTIALS = credentials('credential-test-fr')
		ANYPOINT_BUSINESS_GROUP = "cloudhub organisation"
		ANYPOINT_DEPLOYMENT_REGION = "eu-west-2"
		ANYPOINT_DEPLOYMENT_WORKTYPE = "micro"
		ANYPOINT_DEPLOYMENT_WORKS = "1"
	        MAVEN_HOME = "${maven3}"
	        JAVA_HOME = "${jdk}"
			
      }
      steps {
	      script{
		      if(isUnix()){
        sh '''
	        mvn deploy -P cloudhub -Dmule.version=4.2.2 -Danypoint.username=${ANYPOINT_CREDENTIALS_USR} -Danypoint.password=${ANYPOINT_CREDENTIALS_PSW} -Dcloudhub.application.name=flow-training-example
		-Dcloudhub.env=${ANYPOINT_DEPLOYMENT_DEV_NAME} -Dcloudhub.region=${ANYPOINT_DEPLOYMENT_REGION} -Dcloudhub.worktype=${ANYPOINT_DEPLOYMENT_WORKTYPE}
			      -Dcloudhub.works=${ANYPOINT_DEPLOYMENT_WORKS} -Dcloudhub.businessgroup=${ANYPOINT_BUSINESS_GROUP} 
	   '''	  
		      }
		      else{
		      
		       bat '''
			      
		  mvn deploy -P cloudhub -Dmule.version=4.2.2 -Danypoint.username=${ANYPOINT_CREDENTIALS_USR} -Danypoint.password=${ANYPOINT_CREDENTIALS_PSW} -Dcloudhub.application.name=flow-training-example
		-Dcloudhub.env=${ANYPOINT_DEPLOYMENT_DEV_NAME} -Dcloudhub.region=${ANYPOINT_DEPLOYMENT_REGION} -Dcloudhub.worktype=${ANYPOINT_DEPLOYMENT_WORKTYPE}
			      -Dcloudhub.works=${ANYPOINT_DEPLOYMENT_WORKS} -Dcloudhub.businessgroup=${ANYPOINT_BUSINESS_GROUP} 
				      
			 '''
		      }
      }
      }      
    }
	}
  }
