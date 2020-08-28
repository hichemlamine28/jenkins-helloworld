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
    def userInput = input(id: 'choix1', message: 'JOB ?', parameters: [
    [$class: 'ChoiceParameterDefinition', description: 'description1', name:'input1', choices: '\nTag\nRelease'],

    
    
    ])
     
                
    }catch (err) {
                    def user = err.getCauses()[0].getUser()
                    if ('SYSTEM' == user.toString()) { // SYSTEM means timeout
                        job2= 'release'     // Set default job to 'release'
                    } else {
                        didInput = false
                        job2='release'
                        echo "Aborted by: [${user}]"
                    }
                }            
                
 
      try{          
    def userInput2 = input(id: 'choix2', message: 'Environnement ?', parameters: [
    [$class: 'ChoiceParameterDefinition', description: 'description2', name:'input2', choices: '\nDev\nQualif\nPreprod\nProd'],
    
    
    ])
    
                
    }catch (err) {
                    def user2 = err.getCauses()[0].getUser()
                    if ('SYSTEM' == user2.toString()) { // SYSTEM means timeout
                        env2= 'qualif'     // Set default Environment to 'qualif'
                    } else {
                        didInput = false
                        env2='qualif'
                        echo "Aborted by: [${user}]"
                    }
                } 
 
 
                
    job = userInput 
    env = userInput2
    echo job
    echo env               
                
                
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

