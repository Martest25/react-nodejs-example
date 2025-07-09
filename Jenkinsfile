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
                    withCredentials([usernamePassword(credentialsId: 'docker-hub-repo', passwordVariable: 'PASS', usernameVariable: 'USER')]) {
                        sh """
                            echo \$PASS | docker login -u \$USER --password-stdin
                            docker build -t ${IMAGE_NAME}:${IMAGE_TAG} .
                            docker push ${IMAGE_NAME}:${IMAGE_TAG}
                        """
                    }
                }
            }
        }
    }
}
