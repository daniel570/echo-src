pipeline {
  agent any
  stages {
      stage('Build and Tag'){
          when{
              branch 'master'
          }
          steps{
             sh 'sudo -S docker build -t echoapp .'
             sh 'sudo -S docker tag echoapp:latest gcr.io/develeap/echoapp:1.0."${BUILD_NUMBER}"'
          }
      }
      stage('Publish'){
          when{
              branch 'master'
          }
          steps{
	     sh 'sudo -S /home/danielharsheffer/google-cloud-sdk/bin/docker-credential-gcr configure-docker'
             sh 'sudo -S /home/danielharsheffer/google-cloud-sdk/bin/gcloud docker -- push gcr.io/develeap/echoapp:1.0."${BUILD_NUMBER}"'
             sh 'echo deploy'
          }
      }
  }
}
