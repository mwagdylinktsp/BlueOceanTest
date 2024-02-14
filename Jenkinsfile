pipeline {
  agent any
  stages {
    stage('SCM') {
      steps {
        echo 'buildtest done'
        git(url: 'git@github.com:360CXservices/CICDTest.git', branch: 'DevelopersBranch', credentialsId: 'it')
      }
    }

    stage('build') {
      steps {
        echo 'test stage done'
      }
    }

    stage('notify me') {
      steps {
        echo 'testttttttttt'
      }
    }

  }
}