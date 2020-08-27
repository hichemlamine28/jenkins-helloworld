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
           

                    PROCEDURE = userInput
                   
                   parameters{
                    choice(name: 'choix',
                           choices: '\nDev\nQualif\nPreprod\nProd',
                           description: 'Environnement: ?'
                       
                   }
                   
                   
              
    
        echo "Environnement : ${params.choix}"   // cette variable permet de choisir sur quel serveur on va deployer
        env="${params.choix}"
        
               
  }  
        echo "Environnement : ${params.choix}"   // cette variable permet de choisir sur quel serveur on va deployer
        env="${params.choix}"


   
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
