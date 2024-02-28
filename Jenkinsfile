pipeline {
    agent {
        docker {
            image 'node:16-buster-slim' 
            args '-p 3000:3000' 
        }
    }
    stages {
        stage('Build') { 
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }
        stage('Manual Approval'){
            steps{
                    input message: 'Lanjutkan ke tahap Deploy?', ok: 'Proceed', parameters: [choice(choices: ['Proceed', 'Abort'], description: 'Pilih tindakan', name: 'ACTION')]
            }
        }
          stage('Deploy') { 
            steps {
                sh './jenkins/scripts/deliver.sh' 
                sleep(time: 60, unit: 'SECONDS')
                sh './jenkins/scripts/kill.sh' 
            }
        }
        
    }
}