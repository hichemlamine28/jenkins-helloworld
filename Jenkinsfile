// donner le choix à l'utilisateur, Builder ou Monter de version
def projet_settings = null
def TARGET_ENV = 'dev'
def MCS_CONTAINER_IMAGE_FULLNAME = null
env2=null

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
               
               
     try{          
    def userInput = input(id: 'choix', message: 'some message', parameters: [
    [$class: 'ChoiceParameterDefinition', choices: '\nDev\nQualif\nPreprod\nProd', description: 'description', name:'input'],
    ])
    env = userInput     
                
    }catch (err) {
                    def user = err.getCauses()[0].getUser()
                    if ('SYSTEM' == user.toString()) { // SYSTEM means timeout
                        env2= 'qualif'     // Set default Environment to 'dev'
                    } else {
                        didInput = false
                        //env2='qualif'
                        echo "Aborted by: [${user}]"
                    }
                }            
                
                
                
                
                
                }
            
  }
 
        echo "Environnement : ${env}"          // cette variable permet de choisir sur quel serveur on va deployer 
        echo "Remember Environnement : ${getEnvName()}" // cette variable permet de choisir sur quel serveur on va deployer 
       
   }
   


node {
    stage('clone') {
    git 'https://github.com/hichemlamine28/jenkins-helloworld.git'
        echo "Environnement clone: ${getEnvName()}"  
    }
    stage('build') {
    sh label: '', script: 'javac Main.java'
        echo "Environnement build : ${getEnvName()}"  
    }
    stage('run') {
    sh label: '', script: 'java Main'
        echo "Environnement run: ${getEnvName()}"  
    }
}



def getEnvName() {

if (env2=='qualif'){return env2}
else{
    if(env == "") {
        return "qualif"
    } else if (env == "Qualif") {
        return "qualif"
    } else if (env =="Prod") {
        return "prod"
    } else if (env =="Dev" ) {
        return "dev"
    } else if (env =="Preprod" ) {
        return "preprod"
    }else if (env =="Uat" ) {
        return "uat"
    }else {
        return "no env selected"
    }
  }    
    
    
}

