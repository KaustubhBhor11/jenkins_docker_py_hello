pipeline {
	agent any

	environment{
		DOCKER_IMAGE = 'hello-world-python:latest' // Docker image name
	}
	stages{
		stage('Checkout'){
			steps{
				git branch: 'main', url: 'https://github.com/KaustubhBhor11/jenkins_docker_py_hello.git'
			}
		}
		stage('Docker Build'){
			steps{
				script{
					// Check if Dockerfile exists
					if (fileExists('Dockerfile')){
						bat "docker build -t ${env.DOCKER_IMAGE} ."
					} else{
						error "Dockerfile not found in the workspace. Please create one for your Python application."
						}
				}
			}
		}
		stage('Docker Run (Optional)'){
			steps{
				bat "docker run --rm ${env.DOCKER_IMAGE}"
			}
		}
	}
	post{
		success{
			echo 'python application Docker image built sucessfully.'
		}
		failure{
			echo 'Docker build or run failed.'
		}
	}
}