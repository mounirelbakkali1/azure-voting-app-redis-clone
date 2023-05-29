pipeline {
   agent any
   stages {
      stage('Verify Branch') {
         steps {
            echo "$GIT_BRANCH"
         }
      }
      stage("Docker BUILD"){
            steps{
                sh("docker images -a")
                sh("""
                    cd myApp/
                    docker images -a 
                    docker build -t jenkins/jenkins .
                    docker images -a 
                    cd ..
                    """)
            }
        }
   }
}
