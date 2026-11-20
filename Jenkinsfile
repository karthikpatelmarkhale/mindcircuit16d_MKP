pipeline {

    agent any
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
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'tomcat', path: '', url: 'http://75.101.187.208:8081/')], contextPath: 'RCB VK', war: '**/*.war'
            }
        }		
		
    }
}
