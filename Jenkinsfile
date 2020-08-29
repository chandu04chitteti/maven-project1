def tomcatWeb = 'C:\\apache-tomcat-8.0.3\\webapps' 
def tomcatBin = 'C:\\apache-tomcat-8.0.3\\bin'

pipeline {
	agent any
		
	options{
		timestamps()
	}
	
	stages{
		stage('Compile-Package-create-war-file') {
			steps{				
				
				script{
					// Get maven home path
					   def mvnHome =  tool name: 'Maven', type: 'maven'  
					   echo "mvnHome : $mvnHome"
					   bat "${mvnHome}/bin/mvn package"
				}
				
				
			}
		}
	        stage('Deploy to Tomcat'){
		    steps{

			  script{

				  bat "copy target\\myproj.war \"${tomcatWeb}\\myproj.war\""
      			           echo "Deployment Success.!!!"
      
                                }
		        }
	        }
		stage('Email-Notification'){

		     steps {

		           emailext (
			   mail bcc: '', body: 'THIS IS AN AUTO GENERATED MAIL FROM JENKINS', cc: '', from: '', replyTo: '', subject: 'Email Report', to: 'chandudeul@gmail.com'
				 )
			  }

		     }
				
	       }
	
          }
