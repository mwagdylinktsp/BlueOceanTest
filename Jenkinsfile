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
        echo 'Build Completed'
        sh 'cd C:\inetpub\wwwroot\TestSite\src\VirtoCommerce.Platform.Web\App_Data'
      }
    }

    stage('Test') {
      steps {
        echo 'Test Done'
      }
    }
  }
}
