pipeline{
        agent any
        environment {
                DB_PASSWORD = credentials("DB_PASSWORD")
        }
        stages{
            stage('Clone chaperootodo'){
                steps{
                        sh "rm -rf chaperootodo_client"
                        sh "git clone https://gitlab.com/qacdevops/chaperootodo_client"  
                }
            }
            stage('Install Docker'){
                steps{
                        sh 'bash scripts/install-docker.sh'
                }
            }
            stage('Deply app'){
                steps{
                         sh 'cd chaperootodo_client && sudo docker-compose pull && sudo -E DB_PASSWORD=${DB_PASSWORD} docker-compose up -d'                   
                }
            }
        }
}
