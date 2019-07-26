pileline{
    agent any
    stage ('build servicelet project') {
        staps {
            bat 'mvn clean package'
        }

        post{
            success{
                echo'now archiveing...'
                archiveArtifacts Artifacts : '**/*.war'
            } 
        
        }

    }
    
    stage ('deploy build satgging area '){
        staps{

        build job : 'deploy_stagging_code'
    }
    }


    }