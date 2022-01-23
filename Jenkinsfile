pipeline {
agent {
label {
		label "built-in"
		customWorkspace "/data/project-myapp"
		
		}
		}
		
	stages {
		
		stage ('CLEAN_OLD_M2') {
			
			steps {
				sh "rm -rf /home/saccount/.m2/repository"
				
			}
			
		}
	
		stage ('MAVEN_BUILD') {
		
			steps {
						
						sh "mvn clean package"
			
			}
			
		
		}
		
		stage ('COPY_WAR_TO_Server'){
		
				steps {
						withCredentials([usernamePassword(credentialsId: 'saccount', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
						sh "scp -r '$USERNAME:$PASSWORD'@10.0.2.51:/data/project/wars"

						}
				
				}
		
		
		
		}
	
	
	
	}
		
}