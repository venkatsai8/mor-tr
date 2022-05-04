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
		 git config --global  user.name "venkatsai8"
		 git config --global  user.email "78792754+venkatsai8@users.noreply.github.com"
		 git checkout -b rc
		 git remote set-url origin https://venkatsai8:${password}@https://github.com/venkatsai8/total_new.git
		 git pull origin rc
		 echo "Hello-world" >> a.txt
		 git add a.txt
                 git diff-index --quiet HEAD || git commit -m "Updated with a.txt"
	         git push origin rc
		'''
		}
		
	   }
	}
     }
 }
