pipeline {
   agent none
   stages {
      stage('Verify Branch') {
         steps {
            echo "$GIT_BRANCH"
         }
      }
      stage("maven install"){
         agent {
      	docker {
        	image 'maven:3.5.0'
        }
      }
         steps{
            sh 'mvn clean install'
         }
      
      }
      stage("Docker BUILD"){
            steps{
                sh("docker images -a")
                sh("""
                    cd azure-vote/
                    docker images -a 
                    docker build -t jenkins/jenkins .
                    docker images -a 
                    cd ..
                    """)
            }
        }
   }
}


