@Library ("Shared") _
pipeline {
    agent {label "Vinod"}

    stages {
	stage("Hello"){
	  steps{
	    scripts{
		hello()
		   }
		}
	    }
        stage("Code") {
            steps {
		script{
                clone("https://github.com/LondheShubham153/django-notes-app.git", "dev")
		}
            }
        }
         stage("Build") {
            steps {
		script{
                docker build("notes-app", "latest", "hrithikpatil")
            	}
		}
        }
         stage("Push to DockerHub") {
            steps {
		script{
		  docker_push("notes-app", "latest", "hrithikpatil")
                }
            }
        }
         stage("Deploy") {
            steps {
                echo "This is deploying the code"
                sh "docker compose up -d"
            }
        }
    }
}
