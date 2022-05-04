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

	stage("test"){
	   when {
		 branch 'test'
		}
	   steps{
		withCredentials([usernamePassword(credentialsId: 'bi-mor', passwordVariable: 'password', usernameVariable: 'username')]) {
 		sh '''
		 apt-get update
		 apt-get install -y git
		 apt-get install pandoc -y
		  git config --global user.name "venkatsai8"
		 git config --global user.email "natrajsai7@gmail.com"
		 git checkout -b cc
		 git remote set-url  origin https://${username}:${password}@github.com/venkatsai8/total_new.git
		 echo "Hello-world new erere" >> a.txt
		 git add .
		 git diff-index --quiet HEAD || git commit -m "Added a.txt"
	         git push origin cc	 
		'''
	     }		
	   }

	}


     }
 }
