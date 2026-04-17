@Library ("Shared") _
pipeline{
    agent {label "vinod"}
    
    stages{
        
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        
        stage("Code"){
            steps{
                script{
                clone( "https://github.com/Shivzade/django-notes-app.git", "main")
                }
            }
        }
        stage("Build"){
            steps{
                script{
                docker_build("notes-app", "latest", "shivzade")
                }
            }
        }
        stage("Test"){
            steps{
                script{
                    docker_push("notes-app", "latest", "shivzade")
                }
            }
        }
        stage("Deploy"){
            steps{
                echo "This is Deploy the code"
                sh "docker compose up -d"
            }
        }
    }
}
