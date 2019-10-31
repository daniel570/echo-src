pipeline {
  agent any
  stages {
      stage('Build and Tag'){
          when{
              branch 'dev'
          }
          steps{
             sh 'sudo -S docker build -t echoapp .'
             sh 'sudo -S docker tag echoapp:latest gcr.io/develeap/echoapp:staging-"${GIT_COMMIT}"'
          }
      }
      stage('Publish'){
          when{
              branch 'dev'
          }
          steps{
            sh 'gcloud --version'
            // sh 'sudo usermod -aG docker tomcat'
          //   sh 'sudo -S docker login gcr.io'
//           sh 'sudo ln -s /home/danielharsheffer/google-cloud-sdk/bin/docker-credential-gcr /usr/local/bin/'
//           sh 'docker-credential-gcr configure-docker'
         //    sh 'gcloud auth configure-docker'
//             sh 'sudo -S /home/danielharsheffer/google-cloud-sdk/bin/gcloud docker -- push gcr.io/develeap/echoapp:1.0."${BUILD_NUMBER}"'
//           sh 'sudo -S gcloud docker -- push gcr.io/develeap/echoapp:1.0."${BUILD_NUMBER}"'
             sh 'gcloud docker -- push gcr.io/develeap/echoapp:staging-"${GIT_COMMIT}"'
             sh 'echo deploy'
          }
      }
  }
}

