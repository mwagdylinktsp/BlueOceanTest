opipeline {
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
        dir('C:\\inetpub\\wwwroot\\TestSite\\src\\VirtoCommerce.Platform.Web\\App_Data') {
    // some block
}
      }
    }
    stage('Test') {
      steps {
        
        echo 'Test Completed'
      }
    }
    stage('Deploy') {
      steps {
        bat "\"${tool 'MSBuild'}\" AspDotNetJenkins.sln /p:DeployOnBuild=true /p:DeployDefaultTarget=WebPublish /p:WebPublishMethod=FileSystem /p:SkipInvalidConfigurations=true /t:build /p:Configuration=Release /p:Platform=\"Any CPU\" /p:DeleteExistingFiles=True /p:publishUrl=C:\inetpub\wwwroot\TestSite"
        echo 'Deployment Completed'
      }
    }
  }
}
