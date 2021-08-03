pipeline {
    agent any
    stages {
        stage('login') {
            steps {
                sh 'docker login -u mahmouddabour -p ${DockerPassword}'
            }
        }
        stage('list docker images') {
            steps {
                sh 'docker images'
            }
        }
    }
}