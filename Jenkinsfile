pipeline {
  agent any
  stages {
    stage('SCM') {
      steps {
        git(url: 'git@github.com:mwagdylinktsp/WebAppTest.git', branch: 'main', credentialsId: 'Word-ssh')
      }
    }

  }
}