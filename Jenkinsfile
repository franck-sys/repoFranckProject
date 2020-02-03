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
		ANYPOINT_URI = "https://anypoint.mulesoft.com"
		ANYPOINT_DEPLOYMENT_ENV_DEV = "developement"
		ANYPOINT_DEPLOYMENT_DEV_NAME = "Training"
		ANYPOINT_DEPLOYMENT_ENV_STAGING ="test"
		ANYPOINT_DEPLOYMENT_STAGING_NAME = "test_repo_staging"
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
	         mvn -s deploy -DmuleDeploy -Dusername=${CLOUDHUB_CREDENTIALS_USR} -Dpassword=${ANYPOINT_CREDENTIALS_USR} -Denvironment=Development -Danypoint.platform.client_id=${ANYPOINT_CREDENTIALS_PSW} -Danypoint.platform.client_secret=${ANYPOINT_CREDENTIALS_PSW} -Dencrypt.key=${ENCRYPT_KEY_PSW} -Dcloudhub.application.name=flow-training-example
			'''	  
		      }
		      else{
		      
		             bat '''
		  mvn -s deploy -DmuleDeploy -Dusername=${CLOUDHUB_CREDENTIALS_USR} -Dpassword=${ANYPOINT_CREDENTIALS_USR} -Denvironment=Development -Danypoint.platform.client_id=${ANYPOINT_CREDENTIALS_PSW} -Danypoint.platform.client_secret=${ANYPOINT_CREDENTIALS_PSW} -Dencrypt.key=${ENCRYPT_KEY_PSW} -Dcloudhub.application.name=flow-training-example	
				      
					   '''
		      }
      }
      }      
    }
	}
  }
