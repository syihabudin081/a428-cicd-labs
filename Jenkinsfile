node {
   
    docker.image('node:16-buster-slim').run('-p 3000:3000') {
        
      
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
    }
}
