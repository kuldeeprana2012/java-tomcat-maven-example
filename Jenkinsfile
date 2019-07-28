pileline{
    agent any 
    stages {
           stage ('build servicelet project') {
               staps {
                    bat 'mvn clean package'
                    } 

                post{
                   success{
                       echo 'now archiveing...'

                       archiveArtifacts artifacts : '**/*.war'
                        } 
        
                    }
            }
    
         stage ('deploy build satgging area '){
               staps{
                   build job : 'deploy_stagging_code'
        }
        }
        }

}