pipeline {
    
	agent {
	    node{
	        label 'master'
	    }	    
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
				
     

				echo "#####################################"
				echo "CREATE APK FILE"		
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

