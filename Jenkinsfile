pipeline{
   agent 'slave1'{
        stages {
            stage (update){
                steps{
                        sudo apt-get update 
                          
                    }

                    }
            stage (adding docker official GPG KEY){
                steps{
                        sudo apt-get install ca-certificates curl -y
                        sudo install -m 0755 -d /etc/apt/keyrings -y
                        sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
                        sudo chmod a+r /etc/apt/keyrings/docker.asc

                     }
            }
            stage (adding repo to apt src){
                steps{
                    echo \
                        "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
                        $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
                         sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
                        sudo apt-get update
                }
            }

            stage (install docker){
                steps{
                    sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y
                }
            }
            stage (creating docker group){
                steps{
                    sudo groupadd docker
                }
            }
            stage(adding user to docker grp){
                steps{
                    sudo usermod -aG docker $USER
                    newgrp docker
                }
            }         
        }  
    }  
}