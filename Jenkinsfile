pipeline {
    agent any 
    stages {
        stage('checkout') { 
            steps {
                script {
                 git  'https://github.com/chinnari321/jenkin.git'
            
            }
        }
        }
        stage('build') { 
           steps {
               script {
                sh "mvn clean package"
            }
        }
        }
        stage ('deploy') {
            steps {
                 script {       
                 s3Upload consoleLogLevel: 'INFO', dontWaitForConcurrentBuildCompletion: false, entries: [[bucket: 'bucket203', excludedFile: '', flatten: false, gzipFiles: false, keepForever: false, managedArtifacts: false, noUploadOnFailure: false, selectedRegion: 'us-east-2', showDirectlyInBrowser: false, sourceFile: '**', storageClass: 'STANDARD', uploadFromSlave: true, useServerSideEncryption: false]], pluginFailureResultConstraint: 'SUCCESS', profileName: 'bucket', userMetadata: []
            }
        }
        
post
    {
        success   
        {
            script
            {
                
            mail to:  'chinnaripasupuleti321@gmail.com',
                       subject: "Build + condition pass",
                       body:"Build got success check status @ ${env.BUILD_URL}"
                       
            }
        }
        
          failure
        {
          script 
          {
                mail to:'chinnaripasupuleti321@gmail.com',
                     subject: "Build fail + condition pass",
                     body:"Build got success check status @ ${env.BUILD_URL}"
     
          }
        }
    }
    
        }
        
    }
}
		
		
