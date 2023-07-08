pipeline {
     agent any
     stages {

         stage("Environment"){
            steps{
                withEnv(['PATH+EXTRA=/usr/sbin:/usr/bin:/sbin:/bin']) {  
          sh '''
            //code block
          '''
        }
            }
         }
         stage('Hello'){
                   steps {
                    sh 'echo "Fuck off Hello!!!!!!!!!!!!!!!"'
                   }
         }
         stage('Build') {
             steps {
                 sh 'echo "Hello World"'
                 sh '''
                     echo "Multiline shell steps works too"
                     ls -lah
                 '''
             }
         }      
         stage('Upload to AWS') {
              steps {
                  withAWS(region:'ap-south-1',credentials:'Annamalai') {
                  sh 'echo "Uploading content with AWS creds"'
                      s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'taxi_rides.csv', bucket:'anna-jenkinsupload')
                  }
              }
         }
     }

}
