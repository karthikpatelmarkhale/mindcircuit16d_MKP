pipeline {

    agent any
	tools{
		maven 'maven 3.10.15'
	}
    stages {
	
        stage('Checkout') {
            steps {
                echo 'This stage clones SC from GIT repo'				
				git branch: 'main', url: 'https://github.com/karthikpatelmarkhale/mindcircuit16d_MKP.git'
            }
        }
		
        
        stage('Build Artifact') {
            steps {
                echo 'This stage builds the code using maven'
				sh 'mvn clean install'			
				
            }
        }
		
        stage('Deploy to Tomcat') {
            steps {
                echo 'This stage deploys .war to tomcat webserver'
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'tomcat', path: '', url: 'http://54.224.77.5:8080/')], contextPath: 'MKP VK', war: '**/*.war'
            }
        }		
		
    }
}
