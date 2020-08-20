pipeline {
   agent any
    options {
        skipStagesAfterUnstable()
    }
   stages {
      stage('Build') {
        steps {
          echo 'Building...'
          echo "Running ${env.BUILD_ID} ${env.BUILD_DISPLAY_NAME} on ${env.NODE_NAME} and JOB ${env.JOB_NAME}"
          sh 'make'
        }
   }
   stage('Test') {
     steps {
        echo 'Testing...'
        sh 'make check'
        junit 'reports/**/*.xml'
     }
   }
   stage('Deploy') {
     steps {
       echo 'Deploying...'
       sh 'make publish'
     }
   }
  }
}
