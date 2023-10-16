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
                    echo 'Build done!'
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
                withCredentials([file(credentialsId: '26e63e4f-bdb1-4dbe-aff6-5fff32b84189', variable: 'GOOGLE_APPLICATION_CREDENTIALS')]) {
                    sh '''
                    cat $GOOGLE_APPLICATION_CREDENTIALS | docker login -u _json_key --password-stdin https://gcr.io
                    echo 'Deploying production....'
                    gcloud auth activate-service-account --key-file=$GOOGLE_APPLICATION_CREDENTIALS
                    docker tag myapp gcr.io/software-engineering-401503/myapp
                    docker push gcr.io/software-engineering-401503/myapp
                    '''
                }

            }
        }
    }
}
