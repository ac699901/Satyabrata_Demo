pipeline {
     agent any
	parameters{
          choice(name: 'applicationMAL' , choices: ['Test1','Test2','Test3','E2e'], description: '')
           }
        stages {
		   	stage('Test1_Bounce-Stop') {
			  when {
			       expression { 
                      return params.applicationMAL == 'Test1'
                    }
			     
			    }
	          steps {
	               script {
				       sshagent(credentials : ['tcopitv1']) {
                         echo "----------Shutdown TCOP-GP on Test1----------"
                         sh 'ssh -o StrictHostKeyChecking=no tcopitv1@suomt68i.dev.qintra.com ./Shutdown.sh'
                          sleep 30
                        }
				     
				    } 
	            }
			}
            stage('Test2_Bounce-Stop') {
			  when {
			       expression { 
                      return params.applicationMAL == 'Test2'
                    }
			     
			    }
	          steps {
	               script {
				       sshagent(credentials : ['tcopitv2']) {
                         echo "----------Shutdown TCOP-GP on Test2----------"
                         sh 'ssh -o StrictHostKeyChecking=no tcopitv2@suomt68i.dev.qintra.com ./Shutdown.sh'
                          sleep 30
                        }
				     
				    } 
	            }
			}
            stage('Test3_Bounce-Stop') {
			  when {
			       expression { 
                      return params.applicationMAL == 'Test3'
                    }
			     
			    }
	          steps {
	               script {
				       sshagent(credentials : ['tcopitv3']) {
                         echo "----------Shutdown TCOP-GP on Test3----------"
                         sh 'ssh -o StrictHostKeyChecking=no tcopitv3@suomt68i.dev.qintra.com ./Shutdown.sh'
                          sleep 30
                        }
				     
				    } 
	            }
			}
            stage('E2e_Bounce-Stop') {
			  when {
			       expression { 
                      return params.applicationMAL == 'E2e'
                    }
			     
			    }
	          steps {
	               script {
				       sshagent(credentials : ['tcope2e']) {
                         echo "----------Shutdown TCOP-GP on E2e----------"
                         sh 'ssh -o StrictHostKeyChecking=no tcope2e@suomt68i.dev.qintra.com ./Shutdown.sh'
                          sleep 30
                        }
				     
				    } 
	            }
			}
            stage('Test1_Bounce-start') {
			  when {
			       expression { 
                      return params.applicationMAL == 'Test1'
                    }
			     
			    }
	          steps {
	               script {
				       sshagent(credentials : ['tcopitv1']) {
                         echo "----------Start TCOP-GP on Test1----------"
                         sh 'ssh -o StrictHostKeyChecking=no tcopitv1@suomt68i.dev.qintra.com ./Start.sh'
                          sleep 30
                        }
				     
				    } 
	            }
			}
            stage('Test2_Bounce-start') {
			  when {
			       expression { 
                      return params.applicationMAL == 'Test2'
                    }
			     
			    }
	          steps {
	               script {
				       sshagent(credentials : ['tcopitv2']) {
                         echo "----------Start TCOP-GP on Test2----------"
                         sh 'ssh -o StrictHostKeyChecking=no tcopitv2@suomt68i.dev.qintra.com ./Start.sh'
                          sleep 30
                        }
				     
				    } 
	            }
			}
            stage('Test3_Bounce-start') {
			  when {
			       expression { 
                      return params.applicationMAL == 'Test3'
                    }
			     
			    }
	          steps {
	               script {
				       sshagent(credentials : ['tcopitv3']) {
                         echo "----------Start TCOP-GP on Test3----------"
                         sh 'ssh -o StrictHostKeyChecking=no tcopitv3@suomt68i.dev.qintra.com ./Start.sh'
                          sleep 30
                        }
				     
				    } 
	            }
			}
            stage('E2e_Bounce-Start') {
			  when {
			       expression { 
                      return params.applicationMAL == 'E2e'
                    }
			     
			    }
	          steps {
	               script {
				       sshagent(credentials : ['tcope2e']) {
                         echo "----------Start TCOP-GP on E2e----------"
                         sh 'ssh -o StrictHostKeyChecking=no tcope2e@suomt68i.dev.qintra.com ./Start.sh'
                          sleep 30
                        }
				     
				    } 
	            }
			}
            stage('Test1_URL-Verification') {
			  when {
			       expression { 
                      return params.applicationMAL == 'Test1'
                    }
			     
			    }
	          steps {
	               script {
				       sshagent(credentials : ['ecomtest']) {
                         echo "----------verification TCOP-GP console on Test1----------"
                         sh 'ssh -o StrictHostKeyChecking=no ecomtest@vlodjumpts00.dev.qintra.com ./URL_verification.sh http://suomt68i.dev.qintra.com:6080/tclogin.jsp'
                          echo "URL check Success"
                        }
				     
				    } 
	            }
			}
            stage('Test2_URL-Verification') {
			  when {
			       expression { 
                      return params.applicationMAL == 'Test2'
                    }
			     
			    }
	          steps {
	               script {
				       sshagent(credentials : ['ecomtest']) {
                         echo "----------verification TCOP-GP console on Test2----------"
                         sh 'ssh -o StrictHostKeyChecking=no ecomtest@vlodjumpts00.dev.qintra.com ./URL_verification.sh http://suomt68i.dev.qintra.com:6085/tclogin.jsp'
                          echo "URL check Success"
                        }
				     
				    } 
	            }
			}
            stage('Test3_URL-Verification') {
			  when {
			       expression { 
                      return params.applicationMAL == 'Test3'
                    }
			     
			    }
	          steps {
	               script {
				       sshagent(credentials : ['ecomtest']) {
                         echo "----------verification TCOP-GP console on Test3----------"
                         sh 'ssh -o StrictHostKeyChecking=no ecomtest@vlodjumpts00.dev.qintra.com ./URL_verification.sh http://suomt68i.dev.qintra.com:9365/tclogin.jsp'
                          echo "URL check Success"
                        }
				     
				    } 
	            }
			}
            stage('E2e_URL-Verification') {
			  when {
			       expression { 
                      return params.applicationMAL == 'E2e'
                    }
			     
			    }
	          steps {
	               script {
				       sshagent(credentials : ['ecomtest']) {
                         echo "----------verification TCOP-GP console on E2e----------"
                         sh 'ssh -o StrictHostKeyChecking=no ecomtest@vlodjumpts00.dev.qintra.com ./URL_verification.sh http://suomt68i.dev.qintra.com:6060'
						 echo "URL check Success"
                        }
				     
				    } 
	            }
			}			
		  
		}
		
    }

