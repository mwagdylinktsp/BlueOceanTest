pipeline {
  agent any
  stages {
    stage('SCM') {
      steps {
        git(branch: 'DevelopersBranch', credentialsId: 'Word-ssh', url: 'git@github.com:360CXservices/CICDTest.git')
        echo 'buildtest done'
      }
    }

    stage('build') {
      steps {
        build 'Virto-test'
        echo 'test stage done'
      }
    }

    stage('Test') {
      steps {
        echo 'Test Done'
      }
    }

    stage('IIS disable and dll location') {
      steps {
        sh 'iisreset /stop'
        echo 'IIS Disabled , Folder Located'
      }
    }

  }
}