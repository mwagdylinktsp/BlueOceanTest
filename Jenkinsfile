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

     stage('Restore packages'){
       steps{
         bat "dotnet restore C:\\WagdyData\\jenkins_home\\workspace\\BlueOceanTest_main\\src\\VirtoCommerce.Platform.Web\\VirtoCommerce.Platform.Web.csproj"
       }
      }

     stage('Build'){
       steps{
         bat "dotnet build C:\\WagdyData\\jenkins_home\\workspace\\BlueOceanTest_main\\src\\VirtoCommerce.Platform.Web\\VirtoCommerce.Platform.Web.csproj --configuration Release"
       }
      }

     stage('Publish'){
       steps{
         bat "dotnet publish C:\\WagdyData\\jenkins_home\\workspace\\TestNEW\\test.csproj "
       }
     }
  }
}
