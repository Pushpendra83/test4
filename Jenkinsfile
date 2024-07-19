pipeline{
       agent any
         tools{
                maven  'Maven-auto'
               }

          stages{
               stage('Build'){
                     sh 'mvn clean package'
                       }
                  post{
                      success{
                            echo "Archiving the Artifacts"
     			archiveArtifacts artifacts: '**/*.war'	

                            }
     			}
            stage('Deploy to tomcat server'){
     			steps{
				deploy adapters: [tomcat9(credentialsId: '4', path: '', url: 'http://localhost:8085/')], contextPath: null, war: '**/*.war'
			}
          }  
}


}