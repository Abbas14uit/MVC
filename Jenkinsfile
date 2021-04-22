//def ReleaseDir = "c:\inetpub\wwwroot"
pipeline {
			agent any
			stages {
				stage('Source'){
					steps{
						checkout([$class: 'GitSCM', branches: [[name: '*/main']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'eb30e76e-0b86-42c9-a80b-2b13f220f0ce', url: 'https://github.com/Abbas14uit/MVC.git']]])
					}
				}
				stage('Build') {
    					steps {
    					    bat "\"${tool 'MSBuild'}\" Appz.sln /p:DeployOnBuild=true /p:DeployDefaultTarget=WebPublish /p:WebPublishMethod=FileSystem /p:SkipInvalidConfigurations=true /t:build /p:Configuration=Release /p:Platform=\"Any CPU\" /p:DeleteExistingFiles=True /p:publishUrl=G:\\MVC_publish -dest:iisapp='MVC',computerName='8081/msdeploy.axd?site=MVC',authType='basic',username='visualapp',password='visualapp' -enableRule:AppOffline"
    					}
				}
			}
}