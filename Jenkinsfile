pipeline {
	agent any
	tools {
	    maven "MAVEN3"
	}

	stages {
	    stage('Fetch code') {
            steps {
               git branch: 'vp-rem', url: 'https://github.com/tawfeeq421/vprofile-project.git'
            }

	    }

	    stage('Build'){
	        steps{
	           sh 'mvn install -DskipTests'
	        }

	        post {
	           success {
	              echo 'Now Archiving it...'
	              archiveArtifacts artifacts: '**/target/*.war'
	           }
	        }
	    }

	    stage('UNIT TEST') {
            steps{
                sh 'mvn test'
            }
        }
	}
}
