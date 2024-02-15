pipeline {
  agent any
  stages {
    stage('SCM') {
      steps {
        //git(branch: 'DevelopersBranch', credentialsId: 'Word-ssh', url: 'git@github.com:360CXservices/CICDTest.git')
        echo 'buildtest done'
      }
    }

    stage('build') {
      steps {
        build 'Virto-test'
        echo 'Build Completed'
      }
    }
    stage('Test') {
      steps {
        rmdir C:\Users\mohamed.elziaty\Desktop\test.txt
        echo 'Test Completed'
      }
    }
    stage('Deploy') {
      steps {
        bat "\"${tool 'MSBuild'}\" AspDotNetJenkins.sln /p:DeployOnBuild=true /p:DeployDefaultTarget=WebPublish /p:WebPublishMethod=FileSystem /p:SkipInvalidConfigurations=true /t:build /p:Configuration=Release /p:Platform=\"Any CPU\" /p:DeleteExistingFiles=True /p:publishUrl=C:\\inetpub\\wwwroot\\Test01"
        echo 'Deployment Completed'
      }
    }
  }
}
