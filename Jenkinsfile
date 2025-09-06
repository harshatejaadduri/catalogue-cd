@Library('jenkins-shared-library')_

def configMap = [
    component: "catalogue",
    project: "roboshop"
]

if( ! env.BRANCH_NAME.equalsIgnoreCase('main') ){
    deploymentPipeline(configMap)
}
else{
    echo "Proceed with PROD"
}