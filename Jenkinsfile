@Library("Shared") _
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
                   clone("https://github.com/Shivanshgoyal17/django-notes-app.git","main")
                }
            }
        }
        stage("Build"){
            steps{
                script{
                    docker_build("notes-app", "latest", "devisershivansh")
                }
            }
        }
        stage("Push to Dockerhub"){
            steps{
                script{
                    docker_push("notes-app", "latest", "devisershivansh")
                }
            }
        }
        stage("Deploy"){
            steps{
                echo "This is deploying the code"
                sh "docker compose down"
                sh "docker compose up -d"
            }
        }
    }
}
