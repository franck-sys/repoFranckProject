pipeline {
  agent any
	
  tools {
	jdk 'jdk1.8'
	maven 'maven3'
  }
  
  stages {	  
        stage('find') {
            steps {
                mvn -f /workspacefranck/repoFranckProject/flow/pom.xml 
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
	        mvn -f /workspacefranck/repoFranckProject/flow/pom.xml
	        mvn deploy -P cloudhub -Dmule.version=4.2.2 -Danypoint.username=${ANYPOINT_CREDENTIALS_USR} -Danypoint.password=${ANYPOINT_CREDENTIALS_PSW} -Dcloudhub.application.name=flow-training-example
		
	   '''	  
		      }
		      else{
		      
		       bat '''	
		  mvn -f /workspacefranck/repoFranckProject/flow/pom.xml     
		  mvn deploy -P cloudhub -Dmule.version=4.2.2 -Danypoint.username=${ANYPOINT_CREDENTIALS_USR} -Danypoint.password=${ANYPOINT_CREDENTIALS_PSW} 
				      
			 '''
		      }
      }
      }      
    }
	}
  }
