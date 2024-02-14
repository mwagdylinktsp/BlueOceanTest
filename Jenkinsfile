pipeline {
  agent any
  stages {
    stage('SCM') {
      steps {
        echo 'buildtest done'
        git branch: 'DevelopersBranch', credentialsId: 'Word-ssh', url: 'git@github.com:360CXservices/CICDTest.git'
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
