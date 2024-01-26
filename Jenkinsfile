pipeline {
    agent any
    tools {
	    maven "MAVEN3"
	
	}

    stages{
        stage('Fetch code') {
          steps{
              git branch: 'vp-rem', url:'https://github.com/tawfeeq421/vprofile-project.git'
          }  
        }

        stage('Build') {
            steps {
                sh 'mvn clean install -DskipTests'
            }
            post {
                success {
                    echo "Now Archiving."
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }
        stage('Test'){
            steps {
                sh 'mvn test'
            }

        }

        stage('Checkstyle Analysis'){
            steps {
                sh 'mvn checkstyle:checkstyle'
            }
        }

    }
}
