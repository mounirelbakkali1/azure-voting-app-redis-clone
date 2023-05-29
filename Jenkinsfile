pipeline {
   agent any
   environment {
      DOCKER_HOME = '/user/bin/docker'
   }
   stages {
      stage('Verify Branch') {
         steps {
            echo "$GIT_BRANCH"
         }
      }
      stage("Docker BUILD"){
            steps{
                sh("${DOCKER_HOME} images -a")
                sh("""
                    cd myApp/
                    ${DOCKER_HOME} images -a 
                    ${DOCKER_HOME} build -t jenkins/jenkins .
                    ${DOCKER_HOME} images -a 
                    cd ..
                    """)
            }
        }
   }
}
