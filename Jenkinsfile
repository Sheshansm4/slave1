pipeline{
   agent 'slave1'{
        stages {
            stage (update){
                steps{
                        sudo apt-get update 
                          
                    }

                    }
            stage (install java){
                steps{
                        sudo apt-get install openjdk-11-jdk

                     }
                 
                }
             }
        }
    }