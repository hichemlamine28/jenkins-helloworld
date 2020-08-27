// donner le choix à l'utilisateur, Builder ou Monter de version
def projet_settings = null
def PROCEDURE = 'Test/Build'
def TARGET_ENV = 'dev'
def MCS_CONTAINER_IMAGE_FULLNAME = null

println "BRANCH : " + env.BRANCH_NAME

    properties(
        [
            buildDiscarder(
                    logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '5',numToKeepStr: '5')
            ),
            disableConcurrentBuilds(),
            disableResume(),
            pipelineTriggers([pollSCM('* * * * *')])
        ]
    )

node('master'){

    stage('set environment'){
    //projet_settings =  getConfigObject()
    //USERS_TO_NOTIFY = projet_settings.jenkins.users_to_notify
   
               timeout(time: 30, unit: 'SECONDS') {
                try {
                    def userInput = input(
                            id: 'userInput', message: 'Environnement?', ok: 'Submit', parameters: [
                            [$class: 'ChoiceParameterDefinition', name: 'procedure', description: '', choices: '\nDev\nQualif\nPreprod\nProd'],
                    ]
                    )
                    PROCEDURE = userInput
                } catch (err) {
                    def user = err.getCauses()[0].getUser()
                    if ('SYSTEM' == user.toString()) { // SYSTEM means timeout
                        PROCEDURE = 'Test/Build'     // Set default Environment to 'dev'
                    } else {
                        didInput = false
                        echo "Aborted by: [${user}]"
                    }
                }
    
        echo "Environnement : ${params.procedure}"   // cette variable permet de choisir sur quel serveur on va deployer
        env="${params.procedure}"
        
               
  }  
        echo "Environnement : ${params.procedure}"   // cette variable permet de choisir sur quel serveur on va deployer
        env="${params.procedure}"
       
       // USERS_TO_NOTIFY = 'hichem.elamine@breakpoint-technology.fr'
       // projet_settings =  getConfigObject() 
        
        
        GCP_PROJECT_ID="linkinnov-221611"
        SVN_CREDENTIALS_ID='jenkins'
       // GCP_SERVICE_ACCOUNT_PUSH_ID='jenkins-linkinnov-imagepush'
       // GCP_JSON_SVN_PATH=''
       // GCP_JSON_LOCAL_PATH=''
       // // BUILD_CONTAINER_IMAGE_NAME='mkenney/npm:node-8-debian'
        BUILD_CONTAINER_IMAGE_NAME='node:8-stretch'
        PUSH_CONTAINER_IMAGE_NAME='cloudsdk-maven-java8-docker'
        MCS_DOCKER_REGISTRY_URL = 'eu.gcr.io/'+GCP_PROJECT_ID+'/'
        DOCKERFILE_PATH = './build_scripts/Dockerfile'
        MCS_CONTAINER_IMAGE_FULLNAME='' //do not set. jenkins will set it

   
   }
   
   }



node {
    stage('clone') {
    git 'https://github.com/hichemlamine28/jenkins-helloworld.git'
    }
    stage('build') {
    sh label: '', script: 'javac Main.java'
    }
    stage('run') {
    sh label: '', script: 'java Main'
    }
}
