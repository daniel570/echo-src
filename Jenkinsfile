pipeline {
  agent any
  stages {
      stage('Build and Tag'){
          when{
              branch 'master'
          }
          steps{
             sh 'sudo -S docker build -t echoapp .'
             sh 'sudo -S docker tag echoapp:latest echoapp:1.0."${BUILD_NUMBER}"'
          }
      }
      stage('Publish'){
          when{
              branch 'master'
          }
          steps{
             sh 'gcloud docker -- push gcr.io/develeap/echoapp:1.0."${BUILD_NUMBER}"'
             sh 'echo deploy'
          }
      }
  }
}
