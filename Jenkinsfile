pipeline {
    agent any

    environment {
        VERSION = "1.0.${BUILD_NUMBER}"
        PATH = "${PATH}:${getSonarPath()}"
    }

    stages {
        stage ('Sonarcube Scan') {
        //     steps{
        //     withSonarQubeEnv() { // If you have configured more than one global server connection, you can specify its name
        //     sh "${scannerHome}/bin/sonar-scanner"
        //   }
        //     }
        def scannerHome = tool 'SonarScanner 2.8';
        steps {
        withSonarQubeEnv('SonarQubeScanner') {
          sh "${scannerHome}/bin/sonar-scanner"
        }
        }

}

}
}

def getSonarPath(){
        def SonarHome= tool name: 'sonarqube', type: 'hudson.plugins.sonar.SonarRunnerInstallation'
        return SonarHome
    }


// pipeline {
//   agent any
//   stages {
//     stage('SonarQube analysis') {
//       steps {
//         script {
//           // requires SonarQube Scanner 2.8+
//           scannerHome = tool 'SonarQube Scanner 2.8'
//         }
//         withSonarQubeEnv('SonarQube Scanner') {
//           sh "${scannerHome}/bin/sonar-scanner"
//         }
//       }
//     }
//   }
// }
