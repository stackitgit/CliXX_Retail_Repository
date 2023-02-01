pipeline {
    agent any

    environment {
        VERSION = "1.0.${BUILD_NUMBER}"
        PATH = "${PATH}:${getSonarPath()}:${getDockerPath()}"
    }

    stages {
        stage ('Sonarcube Scan') {
        steps {
         script {
          scannerHome = tool 'sonarqube'
        }
        withCredentials([string(credentialsId: 'SONAR_TOKEN', variable: 'SONAR_TOKEN')]){
        withSonarQubeEnv('SonarQubeScanner') {
          sh " ${scannerHome}/bin/sonar-scanner \
          -Dsonar.projectKey=CliXX-App   \
          -Dsonar.login=${SONAR_TOKEN} "
        }
        }
        }

}

 stage('Quality Gate') {
            steps {
                timeout(time: 3, unit: 'MINUTES') {
                    waitForQualityGate abortPipeline: true
            }
            }
        }


  stage ('Build Jar and Docker and Push') {
          steps {
            script {
             DockerHome = tool 'docker-inst'
             }
              sh "
                 ${DockerHome}/docker build . -t clixx-image:$VERSION              
              "
          }
        }
}

}



def getSonarPath(){
        def SonarHome= tool name: 'sonarqube', type: 'hudson.plugins.sonar.SonarRunnerInstallation'
        return SonarHome
    }
def getDockerPath(){
        def DockerHome= tool name: 'docker-inst', type: 'dockerTool'
        return DockerHome
    }
    

