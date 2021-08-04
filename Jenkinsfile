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

        stage('a3mel el sa7') {
            steps {
                 script {
                    if  (params.BRANCH == 'release') 
                            {
                             sh "git checkout ${params.BRANCH}"
                            sh 'docker build . -t mahmouddabour/jenkinstask:yallabena'
                            sh 'docker push mahmouddabour/jenkinstask:yallabena'
                            
                             }
                     else if  (params.BRANCH == 'prod') 
                            {
                            sh "git checkout ${params.BRANCH}"
                            sh 'docker pull mahmouddabour/jenkinstask:yallabena'
                            sh 'kubectl apply -f deployment.yaml'
                             }
                     else if  (params.BRANCH == 'dev') 
                            {
                            sh "git checkout ${params.BRANCH}"
                            sh 'docker pull mahmouddabour/jenkinstask:yallabena'
                            sh 'kubectl apply -f deployment.yaml'
                             }
                     else (params.BRANCH == 'test') 
                            {
                            sh "git checkout ${params.BRANCH}"
                            sh 'docker pull mahmouddabour/jenkinstask:yallabena'
                            sh 'kubectl apply -f deployment.yaml'
                             }
                   
                 }
            }
        }

    }
}