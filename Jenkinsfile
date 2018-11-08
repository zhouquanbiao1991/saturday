pipeline {
	agent none
	stages {
		stage('build') {
			agent { docker { image python } }
			steps {
				sh 'python -m compileall sources/'
			}
		}
		stage('test') {
			agent { docker { image 'qnib/pytest' } }
			steps {
				sh 'py.test --verbose --junit-xml test-reports/results.xml sources/test_mission.py'
			}
			post {
				always {
					junit 'test-reports/results.xml'
				}
			}
		}
	}
}