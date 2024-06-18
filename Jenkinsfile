pipeline {
  agent any
  /*environment {
                SONAR_URL = 'https://sonarcloud.io/'
                SONAR_ORG = 'devsecops1-kb'
                SONAR_PROJECTKEY = 'devsecops1-kb'
                SONAR_LOGIN = '6388cfceaadf0f5725a5921b0d8dffb0f4648d53'
            }*/
  tools { 
        maven 'Maven_3_2_5'  
    }
   stages{
    stage('CompileandRunSonarAnalysis') {
      /*steps {	
         //     sh "mvn clean verify sonar:sonar -Dsonar.host.url=${env.SONAR_URL} -Dsonar.organization=${env.SONAR_ORG} -Dsonar.projectKey=${env.SONAR_PROJECTKEY} -Dsonar.login=${env.SONAR_LOGIN}"
			}*/
			steps {	
		    sh 'mvn clean verify sonar:sonar -Dsonar.projectKey=devsecops1-kb -Dsonar.organization=devsecops1-kb -Dsonar.host.url=https://sonarcloud.io -Dsonar.token=6388cfceaadf0f5725a5921b0d8dffb0f4648d53'
			}
    }

	stage('RunSCAAnalysisUsingSnyk') {
            steps {		
				withCredentials([string(credentialsId: 'SNYK_TOKEN', variable: 'SNYK_TOKEN')]) {
					sh 'mvn snyk:test -fn'
				}
			}
    }		
  }
}
