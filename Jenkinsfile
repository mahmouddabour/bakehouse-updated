pipeline {
    agent any
    parameters {
        choice(name: 'BRANCH', choices: ['dev', 'test', 'release','prod'])
    }

    stages {
        stage('docker login') {
            steps {
                sh 'docker login -u mahmouddabour -p ${DockerPassword}'
            }
        }

        stage('docker Pull to local image') {
            steps {
                //  script {
                    if  (params.BRANCH == 'release')  {
                            sh 'docker build . -t mahmouddabour/jenkinstask:yallabena'
                            sh 'docker push mahmouddabour/jenkinstask:yallabena' }
                   
                //  }
            }
        }

    }
}