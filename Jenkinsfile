pipeline{
    agent{
        labels 'AGENT-1'
    }
    environment{
        ACC_ID = "513993748676"
        appVersion = ''
        REGION = "us-east-1"
        PROJECT = "roboshop" 
    }
    options{
        disableConcurrentBuilds()
        ansiColor('xterm')
    }
    parameters{
        string(name: 'appVersion', description: 'Image version of the application')
        choice(name: 'deploy_to', choices: ['dev','prod','qa'] , description: 'pick up an environment')
    }
    stages{
        stage('Deploy'){
         steps{
                withAWS(credentials: 'aws-creds', region: 'us-east-1') {
                        sh """
                            aws eks update-kubeconfig --region $REGION --name "k8-$PROJECT-${params.deploy_to}"
                            kubectl get nodes
                            """
                }      
            }

        }
    }
    post{
        always{
            echo "====++++always++++===="
        }
        success{
            echo "====++++only when successful++++===="
        }
        failure{
            echo "====++++only when failed++++===="
        }
    }
}   