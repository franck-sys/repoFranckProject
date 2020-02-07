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
      }
	    
      steps {
	      script{
		      if(isUnix()){
        sh '''
	      
	        mvn clean install
	        mvn deploy -P cloudhub -Dmule.version=4.2.2 -Danypoint.username=${ANYPOINT_CREDENTIALS_USR} -Danypoint.password=${ANYPOINT_CREDENTIALS_PSW} -Dcloudhub.application.name=mulesoft-x-api
		
	   '''	  
		      }
		      else{
		      
		       bat '''
		  mvn clean install     
		  mvn deploy -P cloudhub -Dmule.version=4.2.2 -Danypoint.username=${ANYPOINT_CREDENTIALS_USR} -Danypoint.password=${ANYPOINT_CREDENTIALS_PSW} -Dcloudhub.application.name=mulesoft-x-api
				      
			 '''
		      }
	      }
      }
      }      
    }
}
