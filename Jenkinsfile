pipeline {
    agent any
    stages {
        stage('Test') {
            steps {
                withCredentials([string(credentialsId: 'gcp', variable: 'GOOGLE_APPLICATION_CREDENTIALS')]) {
                    sh '''
                    echo 'Testing..'
                    echo 'why'
                    // gcloud version
                    // gcloud auth activate-service-account --key-file=$GOOGLE_APPLICATION_CREDENTIALS
                    // gcloud compute zone list
                    '''
                }
                
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
