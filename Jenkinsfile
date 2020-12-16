pipeline {
    agent any

    stages {
        stage('Pipeline') {
        	steps{
	            script{
	            	def ejecucion 
	            		switch(params.buildtool){
						case'gradle':
						 ejecucion = load 'gradle.groovy'
						break
						default:
						 ejecucion = load 'maven.groovy'
						break 
					}

					ejecucion.callBuildandTest()
					
					stage('sonar') {
                        def scannerHome = tool 'sonar-scanner';
                        withSonarQubeEnv('sonar') {
                            bat "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=ejemplo-gradle -Dsonar.java.binaries=build" 
                         }                     
                    }
					
					ejecucion.callRun()

					stage('rest'){
						 sleep 10
						 bat 'curl http://localhost:8083/rest/mscovid/estadoMundial'
					}
					stage('nexus'){
						nexusPublisher nexusInstanceId: 'nexus', nexusRepositoryId: 'test-nexus', 
						packages: [[$class: 'MavenPackage', mavenAssetList: [[classifier: '', extension: 'jar', 
						filePath: 'DevOpsUsach2020-0.0.1.jar']], 
						mavenCoordinate: [artifactId: 'DevOpsUsach2020', groupId: 'com.devopsusach2020', packaging: 'jar', version: '0.0.1']]]

					}

	            }
	        }
        }
    }
}
