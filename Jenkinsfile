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
                sh 'docker pull mahmouddabour/jenkinstask:yallabena'
            }
        }
         stage('kube push local image') {
            steps {
                sh 'kubectl apply -f deployment.yaml'
            }
        }
    }


    // stages {
    //     stage('login') {
    //         steps {
    //             sh 'docker login -u mahmouddabour -p ${DockerPassword}'
    //         }
    //     }
    
    //     stage('docker build local image') {
    //         steps {
    //             script{
    //                 if { params.BRANCH == 'release' } {
    //                     sh 'docker build . -t mahmouddabour/jenkinstask:yallabena'
    //                     sh 'docker push mahmouddabour/jenkinstask:yallabena'}
                
    //                 else {params.BRANCH == 'prod' } {
    //                     sh 'git checkout ${params.BRANCH}'
    //                     sh 'sudo cp -R .kube /var/lib/jenkins'
    //                     sh 'sudo chmod 777 /var/lib/jenkins/.kube/config'
    //                     sh 'docker pull mahmouddabour/jenkinstask:yallabena'
    //                     sh 'kubectl apply -f deployment.yaml' }
    //                 }
    //             }
               
    //         }
        
    // }
}