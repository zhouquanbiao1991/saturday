pipeline {
	agent none
	stages {
		stage 'build' {
			agent { docker { python:3.7 } }
			steps {
				sh 'python -m compileall sources/'
			}
		}
		stage 'test' {
			agent { docker { python3-nosetests:latest } }
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