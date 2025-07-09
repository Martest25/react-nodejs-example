pipeline {
    agent any
    tools{
        NodeJS 'NodeJS-24.2.0'
    }

    stages {
        stage (Testing Node and NPM) {
            steps {
                script{
                    sh 'node -v'
                    sh 'npm -v'
                }
            }
        }
    }
}
