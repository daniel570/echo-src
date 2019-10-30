pipeline {
  agent any
  // triggers
  // {
  //     gitlab(
  //     triggerOnPush: true,
  //     triggerOnMergeRequest: true,
  //     branchFilterType: 'All',
  //     addVoteOnMergeRequest: true
  //     )
  // }
  stages {
      stage('Build and Tag'){
          when{
              branch 'master'
          }
          steps{
             sh 'docker build -t echoapp .'
             sh 'docker tag echoapp:latest echoapp:1.0."${BUILD_NUMBER}"'
          }
      }
      stage('Publish'){
          when{
              branch 'master'
          }
          steps{
             //sh 'docker tag echoapp:latest echoapp:1.0."${BUILD_NUMBER}"'
             sh 'echo deploy'
          }
      }
  }
}
