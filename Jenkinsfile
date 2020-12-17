pipeline {
	agent any
	environment {
		GO111MODULES = 'on'
	}
	tools {
		go 'go-1.12'
	}
	stages {
		stage('Build') {
			steps {
				sh 'go build'
			
			}
		}
		stage('Test'){
			environment {
				CODECOV_TOKEN = credentials ('CODECOV_TOKEN')
			}
			steps {
				sh 'go ./.. -coverprofile=coverage.txt'
				sh 'curl -s https//codecov.io/bash | bash -s -'
			}
		}
	}
}