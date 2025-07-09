pipeline {
    agent any

    tools {
        nodejs 'NodeJS-24.2.0'
    }

    environment {
        IMAGE_NAME = 'martest25/react-nodejs-example'
        IMAGE_TAG = 'latest'
        DOCKER_USERNAME = credentials('docker-hub').username
        DOCKER_PASSWORD = credentials('docker-hub').password
    }

    stages {
        stage('Testing Node and NPM') {
            steps {
                script {
                    sh 'node -v'
                    sh 'npm -v'
                }
            }
        }

        stage('Docker build and push') {
            steps {
                script {
                    sh """
                        docker build -t ${IMAGE_NAME}:${IMAGE_TAG} .
                        echo "${DOCKER_PASSWORD}" | docker login -u "${DOCKER_USERNAME}" --password-stdin
                        docker push ${IMAGE_NAME}:${IMAGE_TAG}
                    """
                }
            }
        }
    }
}
