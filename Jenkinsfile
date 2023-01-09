// scripted
// node {
// 		echo "Build"
// 		echo "Test"
// 		echo "Integration Test"
// }

// declartive

pipeline {
		agent any
		stages {
			stage('Build'){
				steps {
					echo "Build"
				}
			}
			stage('Test'){
				steps {
					echo "Test"
				}
			}
			stage('Integration test'){
				steps {
					echo "Integration Test"
				}
			}
		} 
		
		post {
			always {
				echo "I'm awesome. I run always"
			}
			success {
				echo "T run when you are succesful"
			}
			failure {
				echo "T run when you are failed"
			}
		}
		
}
