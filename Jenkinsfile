pipeline {
  agent any
  
  node{
   checkout scm
  }
  
  tools {
	jdk 'jdk1.8'
	maven 'maven3'
  }
  
  stages {
    stage('build'){
	  steps{
             if(isUnix()){	  
		  sh 'make'	 
           archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true 
             }
              else{
			         bat 'make'  
					 archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true  
			  }			 
	  }
	}  
  }
  
  stages {
    stage('Test') { 
      steps {
         if(isUnix()){
		 sh 'make check || true'
		 junit '**/target/*.xml'
		 }
		 else {
		      bat 'make check || true'
		      junit '**/target/*.xml'
		 }
      }
    }
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
