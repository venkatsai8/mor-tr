pipeline {
    agent {
        docker { image 'ubuntu:latest' 
                  args '-u root'
                }
    }
    stages {
        stage("Develop") {
            when {
                branch 'develop'
            }
            steps {
		sh '''
                echo "Hello Im Developer"
                apt-get update
                apt-get install -y python3
               apt-get install  -y pip
               '''

            }
        }
     }
 }
