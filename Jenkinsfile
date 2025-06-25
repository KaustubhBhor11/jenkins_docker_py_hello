pipeline{
    agent any
    
    environment{
        DOCKER_IMAGE='hello-world-python:latest'
    }

    stages{
        stage('Checkout'){
            steps{
                git branch: "main",url: 'https://github.com/KaustubhBhor11/jenkins_docker_py_hello.git'
            }
        }

        stage('Docker Build'){
            steps{
                if (fileExists('Dockerfile')){
                    sh "docker build -t ${env.DOCKER_IMAGE} ."
                }else{
                    error "Dockerfile not found in the workspace. Please create onr for your python application"
                }
            }
        }
        stage('Docker Run (Optional)'){
            steps{
                sh "docker run --rm ${env.DOCKER_IMAGE}"
            }
        }
    }

    post{
        success{
            echo "Pyhton application Docker Image build successfully"
        }failure{
            echo "Docker build or run failed"
        }
    }
}

