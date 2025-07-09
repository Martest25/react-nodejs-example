pipeline {
    agent any

    tools {
        nodejs 'NodeJS-24.2.0'
    }

    environment {
        IMAGE_NAME = 'martest25/react-nodejs-example'
        IMAGE_TAG = 'latest'
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
                    docker.withRegistry('https://index.docker.io/v1/', 'docker-hub-credentials') {
                        def app = docker.build("${env.IMAGE_NAME}:${env.IMAGE_TAG}")
                        app.push()
                    }
                }
            }
        }
    }
}
