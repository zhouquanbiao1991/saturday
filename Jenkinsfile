pipeline {
	agent none
	stages {
		stage('build') {
			agent { docker { image python } }
			steps {
				sh 'python -m compileall sources/'
			}
		}
	}
}