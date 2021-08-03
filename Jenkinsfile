pipeline {
    agent any
    stages {
        stage('login') {
            steps {
                sh 'docker login -u mahmouddabour -p ${DockerPassword}'
            }
        }
        stage('docker build local image') {
            steps {
                sh 'docker build Dockerfile -tag mahmouddabour/jenkinstask:yallabena'
            }
        }
        stage('docker push local image') {
            steps {
                sh 'docker push mahmouddabour/jenkinstask:yallabena'
            }
        }
    }
}