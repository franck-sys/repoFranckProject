pipeline {
  agent any
	
  tools {
	jdk 'jdk1.8'
	maven 'maven3'
  }
	
	
	stages{  
		
		stage ('Initialize') {
            steps {
                bat '''
                    echo "PATH = ${PATH}"
                    echo "MVN_HOME = ${MVN_HOME}"
                '''
            }
        }
		
    stage('Deploy CloudHub') { 
	    
      environment { 
	      
	        ANYPOINT_CREDENTIALS = credentials('credential-test-fr')
	        ANYPOINT_BUSINESS_GROUP = "cloudhub organisation"
		ANYPOINT_URI = "https://anypoint.mulesoft.com"
		ANYPOINT_DEPLOYMENT_ENV_DEV = "developement"
		ANYPOINT_DEPLOYMENT_DEV_NAME = "Training"
		ANYPOINT_DEPLOYMENT_ENV_STAGING ="test"
		ANYPOINT_DEPLOYMENT_STAGING_NAME = "test_repo_staging"
		ANYPOINT_DEPLOYMENT_REGION = "eu-west-2"
		ANYPOINT_DEPLOYMENT_WORKTYPE = "micro"
		ANYPOINT_DEPLOYMENT_WORKS = "1"	
	      
	      
	      
      }
	    
      steps {
	      script{
		      if(isUnix()){
        sh '''
	      
	        mvn clean install
	       mvn deploy -P cloudhub -Dmule.version=4.2.2 -Danypoint.username=${ANYPOINT_CREDENTIALS_USR} -Danypoint.password=${ANYPOINT_CREDENTIALS_PSW} -Dcloudhub.application.name=flow-training-example
		-Dcloudhub.env=${ANYPOINT_DEPLOYMENT_DEV_NAME} -Dcloudhub.region=${ANYPOINT_DEPLOYMENT_REGION} -Dcloudhub.worktype=${ANYPOINT_DEPLOYMENT_WORKTYPE}
			      -Dcloudhub.works=${ANYPOINT_DEPLOYMENT_WORKS} -Dcloudhub.businessgroup=${ANYPOINT_BUSINESS_GROUP} 
		
	   '''	  
		      }
		      else{
		      
		       bat '''
		  mvn clean install     
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
