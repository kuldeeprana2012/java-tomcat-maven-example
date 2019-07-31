pipeline{
    agent any 
    stages {
           stage ('build servicelet project') {
               steps {
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
               steps{
                   build job : 'deploy_stagging_code'
                }
            }

           stage ('Deploy to production'){
               steps{
                   timeout(time:5, unit:'DAYS'){
                       inout message: 'Approve Production Deploy'
                   }
                   

                    build job : 'deploy_to_prod_code'
                }  

                post{
                    success{
                        echo 'Deployement on Production is Sucessful'

                    }
                    failure{
                        echo 'Deployement Failure on prodcution '

                    }
                }      
            }
                

        }
        
    

}