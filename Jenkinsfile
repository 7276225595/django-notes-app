@Library('Shared')_
pipeline{
    agent { label 'vinod'}
    
    stages{
        stage("Code clone"){
            steps{
                sh "whoami" 
            clone("https://github.com/7276225595/django-notes-app.git","main")
            }
        }
        stage("Code Build"){
            steps{
            docker_build("notes-app","latest","vaibhavlokhande1798")
            }
        }  
        stage("Push to DockerHub"){
            steps{
                docker_push(
                        imageName: "vaibhavlokhande1798/notes-app",
                        imageTag: "latest",
                        credentials: "dockerHubCreds"
                )
            }
        }
        stage("Deploy"){
            steps{
                deploy()
            }
        }
        
    }
}
