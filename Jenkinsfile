pipeline {
    agent any 
	 tools {
        maven 'maven'
    }
    stages {
        stage ('Clone') {
	            steps {
	                git branch: 'master', credentialsId: 'github', url: 'https://github.com/ramprasadgk/java-maven.git'
            }
	}
        stage('Build') {
	    
            
		steps{
	     sh "mvn compile"
		}
        }
        
        stage('Test') { 
		
            steps {
              echo "test"
	      sh "mvn -Dmaven.test.failure.ignore=true install"
            }
        }
        stage('Deploy') { 
            steps {
                echo "deploy"
            }
        }
    }
}
