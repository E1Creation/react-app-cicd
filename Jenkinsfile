node{
    withDockerContainer(args: '-p 3000:3000', image: 'node:lts-buster-slim'){
        stage('Build'){
            sh 'npm install'
        }
        stage('Test'){
            sh 'chmod +x ./jenkins/scripts/test.sh'
            sh './jenkins/scripts/test.sh'
        }
        stage("Deploy"){
              sh 'chmod +x ./jenkins/scripts/deliver.sh'
              sh 'chmod +x ./jenkins/scripts/kill.sh'
              sh './jenkins/scripts/deliver.sh'
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                sh './jenkins/scripts/kill.sh'
        }
    }
   
}
   