pipeline {
    agent any
    stages {
        stage('Test') {
            steps {
                withCredentials([file(credentialsId: '26e63e4f-bdb1-4dbe-aff6-5fff32b84189', variable: 'GOOGLE_APPLICATION_CREDENTIALS')]) {
                    sh '''
                    echo 'Testing..'
                    gcloud version
                    gcloud auth activate-service-account --key-file=$GOOGLE_APPLICATION_CREDENTIALS
                    gcloud compute zones list
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
