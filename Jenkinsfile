node{
    withDockerContainer(args: '-p 3000:3000', image: 'node:lts-buster-slim'){
        stage('Build'){
            sh 'npm install'
        }
        stage('Test'){
            sh 'chmod +x ./jenkins/scripts/test.sh'
            sh './jenkins/scripts/test.sh'
        }
         stage("Manual Approval"){
         input message: 'Apakah anda setuju untuk mendeploy aplikasi ke dalam cloud ?'
         }
        stage("Deploy"){
              sh 'chmod +x ./jenkins/scripts/deliver.sh'
              sh 'chmod +x ./jenkins/scripts/kill.sh'
              sh './jenkins/scripts/deliver.sh'
              sh 'sleep 60'
                sh './jenkins/scripts/kill.sh'
        }
    }
   
}
   