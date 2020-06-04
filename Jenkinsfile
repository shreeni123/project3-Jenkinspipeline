pipeline {
    agent any
    stages {
        stage('Lint HTML') {
            steps {
                sh 'tidy -q -e index.html'
            }
        }
        stage('Upload to AWS') {
            steps {
                withAWS(credentials: 'blueocean', region: 'us-east-2') {
		    sh 'echo "Hello World with AWS creds"'
                    s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'shree-static-jenkins-pipeline')
                }
            }
        }
    }
}