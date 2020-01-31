pipeline {
  agent any
  tools {
	jdk 'jdk1.8'
	maven 'maven3'
  }
    
    stage('Deploy CloudHub') { 
      environment {
        ANYPOINT_CREDENTIALS = credentials('anypoint.credentials')
		ANYPOINT_BUSINESS_GROUP = "cloudhub organisation"
		ANYPOINT_URI = "https://anypoint.mulesoft.com"
		ANYPOINT_APPLICATION_NAME = "flow-training-example"
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
        sh 'mvn deploy -P cloudhub -Dmule.version=4.2.2 -Danypoint.username=${franckTeguia} -Danypoint.password=${Franck*2020}' 
		      }
		      else{
		      
		             bat  sh 'mvn deploy -P cloudhub -Dmule.version=4.2.2 -Danypoint.username=${franckTeguia} -Danypoint.password=${Franck*2020}' 
		      }
      }
      }      
    }
  }
}
