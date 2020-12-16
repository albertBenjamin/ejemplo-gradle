pipeline {
    agent any

    stages {
        stage('Pipeline') {
        	steps{
	            script{

					def ejecucion = load 'gradle.groovy'
					ejecucion.callBuildandTest()
					

	            }
	        }
        }
    }
}
