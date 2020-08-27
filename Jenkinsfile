// donner le choix à l'utilisateur, Builder ou Monter de version
def projet_settings = null
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
   
               timeout(time: 30, unit: 'SECONDS') {
           
                    def userInput = input(
                            id: 'userInput', message: 'Environnement?', ok: 'Submit', parameters: [
                            [$class: 'ChoiceParameterDefinition', name: 'procedure', description: 'procedure', choices: '\nDev\nQualif\nPreprod\nProd'],
                    ]
                    )
                    PROCEDURE = userInput
              
    
        echo "Environnement : ${params.procedure}"   // cette variable permet de choisir sur quel serveur on va deployer
        env="${params.procedure}"
        
               
  }  
        echo "Environnement : ${params.procedure}"   // cette variable permet de choisir sur quel serveur on va deployer
        env="${params.procedure}"


   
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
