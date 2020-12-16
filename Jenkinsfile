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
					

	            }
	        }
        }
    }
}
