pipeline { 
     agent any
     stages {
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
                  withAWS(region:'us-east-2',credentials:'aws-static') {
                  sh 'echo "Uploading content to S3"'
                      s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'jenkins-bucket-shouman')
                  }
              }
         }
     } 
}
   
