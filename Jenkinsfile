pipeline {
    agent any
    stages {
        stage('docker login') {
            steps {
                sh 'docker login -u mahmouddabour -p ${DockerPassword}'
            }
        }
        stage('docker Pull to local image') {
            steps {
                sh 'docker pull mahmouddabour/jenkinstask:yallabena'
            }
        }
         stage('kube push local image') {
            steps {
                sh 'kubectl apply -f deployment.yaml'
            }
        }
    }
}