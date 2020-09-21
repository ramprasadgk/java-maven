pipeline {
    agent any 
    stages {
        stage ('Clone') {
	            steps {
	                git branch: 'master', credentialsId: 'github', url: 'https://github.com/ramprasadgk/java-maven.git'
            }
	}
        stage('Build') { 
            steps {
            echo "build"
	    sh "mvn compile"
            }
        }
        
        stage('Test') { 
            steps {
              echo "test"
	      sh "mvn test"
            }
        }
        stage('Deploy') { 
            steps {
                echo "deploy"
            }
        }
    }
}
