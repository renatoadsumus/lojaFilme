pipeline {
    
	agent {
	    node{
	        label 'master'
	    }	    
	}

environment {
        USER_ACCOUNT = sh (returnStdout: true, script: 'whoami | tr -d "\n"')
}	

	stages{  	
	
		stage('Unit Test'){
		
			steps{	

				echo "#####################################"	
				echo "###  UNIT TEST ###"
				echo "#####################################"
			}
		}
		
		stage('Build App'){
		
			steps{	
           

                echo "#####################################"	
                echo "###  BUILD  ###"
                echo "#####################################"                
			
				}		
		}
		
		
		stage('Build Image'){
		
			steps{					
				
				sh (""" eval \$(aws ecr get-login --region us-east-1 --no-include-email) """)
				
				sh(""" docker build -t home . """)
				
				sh(""" docker tag home ${env.ID_AWS}.dkr.ecr.us-east-1.amazonaws.com/home """)
				
				

				echo "#####################################"
				echo "CREATE DOCKER IMAGE"		
				echo "#####################################"
			}		
		}

        stage('Deploy Image ECR'){
		
			steps{	

				sh(""" docker push ${env.ID_AWS}.dkr.ecr.us-east-1.amazonaws.com/home """)

				echo "#####################################"
				echo " DEPLOY ECR IMAGE"		
				echo "#####################################"
			}		
		}

         stage('Deploy ECS'){
		
			steps{	
			

				echo "#####################################"
				echo "DEPLOY CLUSTER ECS"		
				echo "#####################################"

				sh (""" aws ecs update-service --cluster \"cluster-devops-latam\" --service \"home-service\" --force-new-deployment --region us-east-1 """)
			}		
		}
	}

	post {
        always {   
		  //cleanWs()
          echo "Eliminando..."
        }
    }	
}
