// scripted
// node {
// 		echo "Build"
// 		echo "Test"
// 		echo "Integration Test"
// }

// declartive

pipeline {
	agent any
		// agent {
		// 	docker {
		// 		image 'maven:3.8.7'
		// 	}
		// }
		environment {
			dockerHome = tool "mydocker"
			mavenHome = tool "myMaven"
			PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
		}
		stages {
			stage('Checkout'){
				steps {
					sh 'mvn --version'
					sh 'docker version'
					echo "Build"
					echo "$PATH"
					echo "BUILD_NUMBER - $env.BUILD_NUMBER"
					echo "BUILD_ID - $env.BUILD_ID"
					echo "JOB_NAME - $env.JOB_NAME"
					echo "BUILD_TAG - $env.BUILD_TAG"
					echo "BUILD_URL - $env.BUILD_URL"
				}
			}
			stage('Compile'){
				steps {
					sh "mvn clean compile"
				}
			}
			stage('Test'){
				steps {
					sh "mvn test"
				}
			}
			stage('Integration test'){
				steps {
					sh "mvn failsafe:integration-test failsafe:verify"
				}
			}
			stage('Package'){
				steps {
					sh "mvn package -DskipTests"
				}
			}

			stage('Build Docker image'){
				steps {
					//docker build -t singh2311/currency-exchange-azure:$env.BUILD_TAG
					script {
						dockerImage = docker.build("singh2311/currency-exchange-azure:${env.BUILD_TAG}")
					}
				}
			}
			stage('Push Docker image'){
				steps {
					script {
						docker.withRegistry('','dockerhub') {
								dockerImage.push();
								dockerImage.push('latest');
						}
					}
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
