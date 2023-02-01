pipeline {
    agent any

    environment {
        VERSION = "1.0.${BUILD_NUMBER}"
    }

    stages {
        stage ('Sonarcube Scan') {
            steps {
                sh ''' echo "This is the Sonarcube Scan step!!" '''

	        }
        }
        
	    // stage('Quality Gate') {
        //     steps {
        //         timeout(time: 3, unit: 'MINUTES') {
        //             waitForQualityGate abortPipeline: true
        //         }
        //     }
        // }

      stage ('Build Jar and Docker and Push') {
          steps {
             sh '''
                 echo "Ths is Step 2"
              '''
            }
          }
        }

      stage('Step 3') {
        steps {
         sh ''' "echo This is Step 3" '''
        }
      }

      stage('Step 4') {
        steps {
            sh ''' "echo This is Step 4" '''
        }
      }
    }