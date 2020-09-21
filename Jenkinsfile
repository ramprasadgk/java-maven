pipeline {
    agent any 
    stages {
        stage ('Clone') {
	            steps {
	                git branch: env.BRANCH_NAME, credentialsId: 'github', url: 'https://github.com/ramprasadgk/java-maven.git'
            }
	}
        stage('Build') { 
            steps {
            echo "build"
            }
        }
        
        stage('Test') { 
            steps {
              echo "test"
            }
        }
        stage('Deploy') { 
            steps {
                echo "deploy"
            }
        }
    }
}
