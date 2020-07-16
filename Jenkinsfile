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
			

				sh(""" docker ps """)	

 				echo "USER: ${USER_ACCOUNT}"

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
				
     
				sh(""" docker build -t latam/home:latest . """)

				echo "#####################################"
				echo "CREATE DOCKER IMAGE"		
				echo "#####################################"
			}		
		}

        stage('Deploy Image ECR'){
		
			steps{	


				echo "#####################################"
				echo "FUNCTIONAL TEST DEVICE FARM"		
				echo "#####################################"
			}		
		}

         stage('Deploy ELB'){
		
			steps{	
			

				echo "#####################################"
				echo "DEPLOY APPCENTER"		
				echo "#####################################"
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

