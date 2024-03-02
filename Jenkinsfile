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
        bat 'iisreset /stop'
        powershell 'Copy-Item -Path C:\\WagdyData\\jenkins_home\\workspace\\BlueOceanTest_main\\src\\VirtoCommerce.Platform.Web\\bin\\Debug\\net6.0\\* -Destination D:\\iis\\Virto -Recurse -Force'
        powershell 'Remove-Item D:\\iis\\Virto\\App_Data\\modules\\* -Recurse -Force'
        bat 'iisreset /start'
        powershell 'Copy-Item -Path E:\\share\\New_folder\\* -Destination  D:\\iis\\Virto -Recurse -Force'
      }
    }

    stage('Confirmation ') {
      steps {
        echo 'Project is Running with the New Release'
      }
    }

  }
  environment {
    dotnet = 'C:\\Program Files\\dotnet\\dotnet.exe'
  }
}