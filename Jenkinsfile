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
               sudo docker build -t khalil10/studentlistimage .
               cd ..
            """)
         }
      }





   }
}