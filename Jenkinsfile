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

}

}