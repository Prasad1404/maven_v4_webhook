	pipeline
	{
		agent any
		stages
		{
			stage('ContDownload')
			{
				steps
				{
					git 'https://github.com/Prasad1404/maven_v2.git'
				}

			}
			stage('ContBuild')
			{
				steps
				{
					sh 'mvn package'
				}

			}
			stage('ContDeploy')
			{
				steps
				{
					deploy adapters: [tomcat9(credentialsId: 'd2e2fa2c-ec5b-45e1-9614-96a94446323a', path: '', url: 'http://172.31.10.121:8080')], contextPath: 'testApp', war: '**/*.war'
				}

			}	
			stage('ContTesting')
			{
				steps
				{
						git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
						sh 'java -jar /var/lib/jenkins/workspace/scriptedPipeline1/testing.jar'
				}

			}
			stage('ContDelivery')
			{
				steps
				{
						deploy adapters: [tomcat9(credentialsId: '109952cb-c3a2-4bad-8abc-9e7f0a075818', path: '', url: 'http://172.31.4.63:8080')], contextPath: 'testApp', war: '**/*.war'
				}

			}
		}

	}
	
