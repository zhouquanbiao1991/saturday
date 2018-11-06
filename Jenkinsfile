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
			agent { docker { image python3-nosetests } }
			steps {
				sh 'nosetests --cover-xml-file=test_reports/cover.xml --xunit-file=test_reports/xunit.xml --with-xunit'
			}
			post {
				always {
					xunit 'test_reports/xunit.xml'
				}
			}
		}
	}
}