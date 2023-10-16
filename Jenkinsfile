pipeline {
    agent any
    stages {
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Build') {
            steps {
                sh '''
                    echo 'Building..'
                    docker build -t myapp .
                '''
            }
        }
        stage('Deploy Staging') {
            steps {
                echo 'Deploying staging....'

            }
        }
        stage('Deploy Production') {
            steps {
                sh '''
                echo 'Deploying production....'
                docker tag myapp gcr.io/software-engineering/backend
                docker push gcr.io/software-engineering/backend
                '''

            }
        }
    }
}
