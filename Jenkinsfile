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
                sh 'docker build .'
            }
        }
        stage('docker tag local image') {
            steps {
                sh 'docker -tag mahmouddabour/jenkinstask:yallabena'
            }
        }
         stage('docker push local image') {
            steps {
                sh 'docker push mahmouddabour/jenkinstask:yallabena'
            }
        }
    }
}