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
  
               def IMAGE_TAG = input message: 'Please select a Version', ok: 'Next',
               parameters: [choice(name: 'IMAGE_TAG', choices: '\nDev\nQualif\nPreprod\nProd')]
 
                }
        
         echo "Selected Version = ${env.SELECTED_IMAGE_TAG}"
    
        echo "Environnement : ${params.IMAGE_TAG}"   // cette variable permet de choisir sur quel serveur on va deployer 

               
  }
 
        echo "Environnement : ${params.IMAGE_TAG}"   // cette variable permet de choisir sur quel serveur on va deployer 
        env="${params.IMAGE_TAG}"

   
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

