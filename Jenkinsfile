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
            sh(script: 'docker images -a')
            sh(script: """
               cd simple_api/
               docker images -a
               docker build -t khalil10/studentlistimage .
               docker images -a
               cd ..
            """)
         }
      }





   }
}