pipeline {
    agent any
    parameters {
        choice(name: 'BRANCH', choices: ['dev', 'test', 'release','prod'])
    }

    stages {
        stage('login') {
            steps {
                sh 'docker login -u mahmouddabour -p ${DockerPassword}'
            }
        }
    
        stage('docker build local image') {
            steps {
                script{
                if (env.BRANCH == 'release')
                sh 'docker build . -t mahmouddabour/jenkinstask:yallabena'
                sh 'docker push mahmouddabour/jenkinstask:yallabena'
                }
                else if (env.BRANCH == 'prod') {
                    sh 'git checkout prod'
                    sh 'sudo cp -R .kube /var/lib/jenkins'
                    sh 'sudo chmod 777 /var/lib/jenkins/.kube/config'
                sh 'docker pull mahmouddabour/jenkinstask:yallabena'
                 sh 'kubectl apply -f deployment.yaml'
                
                }
            }
        }
         stage('docker push local image') {
            steps {
                sh 'docker push mahmouddabour/jenkinstask:yallabena'
            }
        }
    }
}