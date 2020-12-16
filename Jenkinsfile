pipeline {
    agent any

    stages {
        stage('Pipeline') {
        	steps{
	            script{
	            		switch(params.buildtool){
						case'gradle':
						def ejecucion = load 'gradle.groovy'
						break
						default:
						def ejecucion = load 'maven.groovy'
						break 
					}

					ejecucion.callBuildandTest()
					

	            }
	        }
        }
    }
}
