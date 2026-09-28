@Library('jenkins-shared-lib') _

properties([
    parameters([
        choice(
            name: 'ENVIRONMENT',
            choices: ['dev', 'qa', 'prod'], // dev will be the default value
            description: 'Target environment'
        ),
        booleanParam(
            name: 'DEPLOY',
            defaultValue: true, // set to false if dont want to deply, set to true if you want to deploy
            description: 'Deploy to EKS after build?'
        )
    ])
])

def configMap = [
    project: "roboshop",
    component: "payment",
    deploy: (params.DEPLOY),
    environment: (params.ENVIRONMENT)
]

if ( ! env.BRANCH_NAME.equalsIgnoreCase("main") ){
    pythonEKSPipeline(configMap)
}
else {
    echo "need permision"
}