pipeline {
  agent any
  stages {
    stage('Checkout Stage') {
      steps {
        git(url: 'git@github.com:mwagdylinktsp/VirtoTest.git', branch: 'main', credentialsId: 'Word-ssh')
      }
    }

    stage('Build Stage') {
      steps {
        bat 'cd\\'
        bat 'C:\\WagdyData\\jenkins_home\\workspace\\BlueOcean_main\\VirtoCommerce.Platform.sln --configuration Release'
        bat 'cd windows\\system32'
      }
    }

    stage('Release Stage') {
      steps {
        bat 'dotnet build %WORKSPACE%\\VirtoCommerce.Platform.sln /p:PublishProfile=" %WORKSPACE%\\TestNEW\\Properties\\PublishProfiles\\FolderProfile.pubxml" /p:Platform="Any CPU" /p:DeployOnBuild=true /m'
      }
    }

    stage('Deploy Stage') {
      steps {
        bat 'net stop "w3svc"'
        bat '"C:\\Program Files (x86)\\IIS\\Microsoft Web Deploy V3\\msdeploy.exe" -verb:sync -source:package="%WORKSPACE%\\JenkinsWebApplicationDemo\\bin\\Debug\\net8.0\\JenkinsWebApplicationDemo.zip" -dest:auto -setParam:"IIS Web Application Name"="TestNEW" -skip:objectName=filePath,absolutePath=".\\\\PackagDemoeTmp\\\\Web.config$" -enableRule:DoNotDelete -allowUntrusted=true'
        bat 'net start "w3svc"'
      }
    }

  }
  environment {
    dotnet = 'C:\\Program Files\\dotnet\\dotnet.exe'
  }
}