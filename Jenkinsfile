pipeline {
   agent any

   stages {
      stage('Verify Branch') {
         steps {
            echo "$GIT_BRANCH"
         }
      }
      stage('Docker Build') {
         steps {
            sh(script: """
               cd simple_api/
               docker build -t khalil10/studentlistimage .
               cd ..
            """)
         }
      }
stage('Push container'){
          steps{
              dir("$WORKSPACE/simple_api"){
                 script{
                    docker.withRegistry('https://index.docker.io/v1/ ', 'dockerhub') {
                    def image = docker.build('khalil10/studentlistrepo:latest')
                    image.push()
                    }
              }
              }
          }
}
stage(' app Deploy'){
   ansiblePlaybook credentialsId: 'appserver', installation: 'ansible', inventory: 'dev.inv', playbook: 'playbook.yml'
}




   }
}