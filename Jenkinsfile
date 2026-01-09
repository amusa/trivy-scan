pipeline {
	agent any

	stages {
		stage('Trivy Image Scanner') {
			agent {
				dockerfile {
					filename 'Dockerfile.docker'
					args '--entrypoint='
				}
			}
			steps {
				sh "trivy help && trivy --cache-dir /tmp/trivy/ image -f json -o results.json 'ayemi/bmi-calc:1.0'"
				recordIssues(tools: [trivy(pattern: 'results.json')])
			}
		}
	}
}