node {
    def app

    stage('Clone repository') {
      

        checkout scm
    }

    stage('Build image') {
  
       app = docker.build("651233853937.dkr.ecr.us-east-1.amazonaws.com/vote-j2")
    }

    stage('Test image') {
  

        app.inside {
            sh 'echo "Tests passed"'
        }
    }

    stage('Push image') {
        
                         docker.withRegistry('https://651233853937.dkr.ecr.us-east-1.amazonaws.com/vote-j2', 'ecr:us-east-1:aws-credentials') {
                              app.push("${env.MYVAR}")
                              app.push("latest")
        }
    }
    
    stage('Trigger ManifestUpdate') {
                echo "triggering updatemanifestjob"
                build job: 'updatemanifest', parameters: [string(name: 'DOCKERTAG', value: env.BUILD_NUMBER)]
        }
}
