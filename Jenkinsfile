// scripted
// node {
// 		echo "Build"
// 		echo "Test"
// 		echo "Integration Test"
// }

// declartive

pipeline {
		agent {
			docker {
				image 'maven:3.8.7'
			}
		}
		stages {
			stage('Build'){
				steps {
					sh 'mvn --version'
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
