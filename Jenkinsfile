pipeline {
  agent any
  environment {
    dotnet = 'C:\\Program Files\\dotnet\\dotnet.exe'
     }
  stages {
    stage('Checkout Stage') {
      steps {
        git(url: 'git@github.com:mwagdylinktsp/VirtoTest.git', branch: 'main', credentialsId: 'Word-ssh')
      }
    }

    stage('Build Stage') {
      steps {
        bat 'D:\\wagdyTest\\VirtoCommerce.Platform.sln --configuration Release'
      }
    }

    stage('Release Stage') {
      steps {
        bat 'dotnet build %WORKSPACE%\\VirtoCommerce.Platform.sln /p:PublishProfile=" %WORKSPACE%\\TestNEW\\Properties\\PublishProfiles\\FolderProfile.pubxml" /p:Platform="Any CPU" /p:DeployOnBuild=true /m'
      }
    }

    stage('Deploy Stage') {
      steps {
        bat '''start cmd.exe
            iisreset /stop
            "C:\\Program Files (x86)\\IIS\\Microsoft Web Deploy V3\\msdeploy.exe" -verb:sync -source:package="%WORKSPACE%\\JenkinsWebApplicationDemo\\bin\\Debug\\net8.0\\JenkinsWebApplicationDemo.zip" -dest:auto -setParam:"IIS Web Application Name"="TestNEW" -skip:objectName=filePath,absolutePath=".\\\\PackagDemoeTmp\\\\Web.config$" -enableRule:DoNotDelete -allowUntrusted=true
            iisreset /start'''
      }
    }

  }
}
