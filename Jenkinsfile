pipeline {
  agent any
  stages {
    stage('Checkout Stage') {
      steps {
        git(url: 'git@github.com:mwagdylinktsp/VirtoTest.git', branch: 'main', credentialsId: 'Word-ssh')
      }
    }

    stage('Release Stage') {
      steps {
        bat 'dotnet build %WORKSPACE%\\src\\VirtoCommerce.Platform.Web\\VirtoCommerce.Platform.Web.csproj'
      }
    }

    stage('Deploy Stage') {
      steps {
        bat '''iisreset /stop
            "C:\\Program Files (x86)\\IIS\\Microsoft Web Deploy V3\\msdeploy.exe" -verb:sync -source:package="%WORKSPACE%\\JenkinsWebApplicationDemo\\bin\\Debug\\net8.0\\JenkinsWebApplicationDemo.zip" -dest:auto -setParam:"IIS Web Application Name"="TestNEW" -skip:objectName=filePath,absolutePath=".\\\\PackagDemoeTmp\\\\Web.config$" -enableRule:DoNotDelete -allowUntrusted=true
            iisreset /start'''
      }
    }

  }
  environment {
    dotnet = 'C:\\Program Files\\dotnet\\dotnet.exe'
  }
}