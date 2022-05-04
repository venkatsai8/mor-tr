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
                apt-get -y python3
               apt-get -y pip
               '''

            }
        }
     }
 }
