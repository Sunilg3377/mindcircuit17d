pipeline {
    agent any

    stages {
       
	   stage('Clone scm') {
            steps {
                echo 'clone code from git repository'
			    git branch: 'main', url: 'https://github.com/Sunilg3377/mindcircuit17d.git'
				
				
            }
        }
		 stage('Build artifact') {
            steps {
                echo 'maven build'
				sh 'mvn clean install'
            }
        }
		
		 stage('deploy to webserver') {
            steps {
                echo 'deploy to tomactserver'
				deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'tomcat', path: '', url: 'http://ec2-18-232-163-89.compute-1.amazonaws.com:8080/')], contextPath: 'MC', war: '**/*.war'
				
				
            }
        }
    }
}
