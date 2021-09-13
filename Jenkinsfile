pipeline {
     agent any
     parameters{
          choice(name: 'applicationMAL' , choices: ['Test1','Test2','Test3','E2e'], description: '')
     }
              stages {
         stage ('Bounce-Stop') {
               steps{
                  script {
                      if("${applicationMAL}" =="Test1")
		        {
			    stage ("Test1_Bounce-Stop") {
		                sshagent(credentials : ['tcopitv1']) {
                                    echo "----------Shutdown TCOP-GP on Test1----------"
                                    sh 'ssh -o StrictHostKeyChecking=no tcopitv1@suomt68i.dev.qintra.com ./Shutdown.sh'
                                    sleep 30
				 }  
			    }   
                        }else if("${applicationMAL}" =="Test2")
                          {
                            stage ("Test2_Bounce-Stop") {  
                                sshagent(credentials : ['tcopitv2']) {
                                   echo "----------Shutdown TCOP-GP on Test2----------"
                                   sh 'ssh -o StrictHostKeyChecking=no tcopitv2@suomt68i.dev.qintra.com ./Shutdown.sh'
                                   sleep 30
                                }   
                           }
                        }else if("${applicationMAL}" =="Test3")
                           {
                            stage ("Test3_Bounce-Stop") {   
                                 sshagent(credentials : ['tcopitv3']) {
                                    echo "----------Shutdown TCOP-GP on Test3----------"
                                    sh 'ssh -o StrictHostKeyChecking=no tcopitv3@suomt68i.dev.qintra.com ./Shutdown.sh'
                                    sleep 30
                                }    
                           }   
                        }else if("${applicationMAL}" =="E2e")
                           {
                            stage ("E2e_Bounce-Stop") {   
                                sshagent(credentials : ['tcope2e']) {
                                   echo "----------Shutdown TCOP-GP on E2e----------"
                                   sh 'ssh -o StrictHostKeyChecking=no tcope2e@suomt68i.dev.qintra.com ./Shutdown.sh'
                                   sleep 30
                                }   
                           }      
                        }
                    }
                }
            }
			stage ('Bounce-start') {
			    steps{
                  script {
                      if("${applicationMAL}" =="Test1")
                         {
                            stage ('Test1_Bounce-start') {  
                                sshagent(credentials : ['tcopitv1']) {
                                 echo "----------Start TCOP-GP on Test1----------"
                                  sh 'ssh -o StrictHostKeyChecking=no tcopitv1@suomt68i.dev.qintra.com ./Start.sh'
                                  sleep 30
                                }  
                            }
                        }else if("${applicationMAL}" =="Test2")
                          {
                           stage ('Test2_Bounce-start') {  
                                sshagent(credentials : ['tcopitv2']) {
                                   echo "----------Start TCOP-GP on Test2----------"
                                    sh 'ssh -o StrictHostKeyChecking=no tcopitv2@suomt68i.dev.qintra.com ./Start.sh'
                                    sleep 30
                                }    
                           }
                        }else if("${applicationMAL}" =="Test3")
                           {
                            stage ('Test3_Bounce-start') {   
                                sshagent(credentials : ['tcopitv3']) {
                                   echo "----------Start TCOP-GP on Test3----------"
                                   sh 'ssh -o StrictHostKeyChecking=no tcopitv3@suomt68i.dev.qintra.com ./Start.sh'
                                   sleep 30
                                }   
                           }   
                        }else if("${applicationMAL}" =="E2e")
                           {
                            stage ('E2e_Bounce-start') {
                                sshagent(credentials : ['tcope2e']) {
                                  echo "----------Start TCOP-GP on E2e----------"
                                  sh 'ssh -o StrictHostKeyChecking=no tcope2e@suomt68i.dev.qintra.com ./Start.sh'
                                  sleep 30
                                }  
                           }      
                        }
                    }
                }
			}
			stage ('URL-Verification') {
			   steps{
                  script {
                      if("${applicationMAL}" =="Test1")
                         {
                            stage ('Test1_URL-Verification') { 
                                sshagent(credentials : ['ecomtest']) {
                                  echo "----------verification TCOP-GP console on Test1----------"
                                   sh 'ssh -o StrictHostKeyChecking=no ecomtest@vlodjumpts00.dev.qintra.com ./URL_verification.sh http://suomt68i.dev.qintra.com:6080/tclogin.jsp'
                                   echo "URL check Success"
                                }   
                            }
                        }else if("${applicationMAL}" =="Test2")
                          {
                            stage ('Test2_URL-Verification') {
                                sshagent(credentials : ['ecomtest']) {
                                   echo "----------verification TCOP-GP console on Test2----------"
                                   sh 'ssh -o StrictHostKeyChecking=no ecomtest@vlodjumpts00.dev.qintra.com ./URL_verification.sh http://suomt68i.dev.qintra.com:6085/tclogin.jsp'
                                   echo "URL check Success"
                                }   
                           }
                        }else if("${applicationMAL}" =="Test3")
                           {
                            stage ('Test3_URL-Verification') {   
                                sshagent(credentials : ['ecomtest']) {
                                   echo "----------verification TCOP-GP console on Test3----------"
                                   sh 'ssh -o StrictHostKeyChecking=no ecomtest@vlodjumpts00.dev.qintra.com ./URL_verification.sh http://suomt68i.dev.qintra.com:9365/tclogin.jsp'
                                   echo "URL check Success"
                                }   
                           }   
                        }else if("${applicationMAL}" =="E2e")
                           {
                            stage ('E2e_URL-Verification') {   
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
        }
}
