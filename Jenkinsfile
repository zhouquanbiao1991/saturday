pipeline {
	agent none
	stages {
		stage 'build' {
			agent { docker { python:latest } }
			steps {
				sh 'python -m compileall sources/'
			}
		}
		stage {
			agent {  }
		}
	}
}