pipeline {
    agent any
    options {
        skipStagesAfterUnstable()
    }
   
    stages {
         stage('Clone repository') { 
            steps { 
                script{
                checkout scm
                }
            }
        }

        stage('Build') { 
            steps { 
                script{
                 app = docker.build("vote-j2")
                }
            }
        }
        stage('Test'){
            steps {
         script {
      myVar = "bbb"
    }
               sh 'echo $myVar'
            }
        }
        stage('Deploy') {
            steps {
                script{
                   
                    
                        docker.withRegistry('https://651233853937.dkr.ecr.us-east-1.amazonaws.com/vote-j2', 'ecr:us-east-1:aws-credentials') {
                              app.push("${env.BUILD_NUMBER}")
                              app.push("latest")
                    }
                }
            }
        }
 stage('Trigger ManifestUpdate'){
            steps {
                 echo "triggering updatemanifestjob"
                build job: 'updatemanifest', parameters: [string(name: 'DOCKERTAG', value: env.BUILD_NUMBER)]
            }
        }



        
    }
}
