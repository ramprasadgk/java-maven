pipeline {
    agent any
    stages {
        stage ('Clone') {
            steps {
                git branch: env.BRANCH_NAME, credentialsId: 'github', url: 'https://github.com/AtlasWD/Atlas.git'
            }
        }
        stage ('env'){
            steps {
                echo "bracnh : ${env.GIT_URL}"
                
            }
        }
       

        stage ('Done') {
            steps {
                script{
			
			
			def GH_URL = env.GIT_URL
  			GIT_HOME = tool 'git_win'
			cleanWs()
                        if ((env.BRANCH_NAME =~ /Release.*/)){
				input(id: "Deploy to production?", message: "Deploy to Prod", ok: 'Deploy')
                    		echo 'Deployed to production'
				
				STDOUT = bat label: "Cloning Repo ${GH_URL}",
				returnStdout: true,
				script:""" ${GIT_HOME} clone ${GH_URL} ."""
				echo STDOUT
				
				STDOUT = bat label: "git fetch all ${GH_URL}",
				returnStdout: true,
				script:""" ${GIT_HOME} fetch --all"""
				echo STDOUT
				
				
				
				STDOUT = bat label: "git checkout branch",
				returnStdout: true,
					script:""" ${GIT_HOME} checkout  ${env.BRANCH_NAME}"""
				echo STDOUT
				
				STDOUT = bat label: "git checkout master",
				returnStdout: true,
				script:""" ${GIT_HOME} checkout master"""
				echo STDOUT
				
				STDOUT = bat label: "git merge branch",
				returnStdout: true,
					script:""" ${GIT_HOME} merge ${env.BRANCH_NAME}"""
				echo STDOUT
				
				STDOUT = bat label: "Pushing Branch master",
				returnStdout: true,
				script:""" ${GIT_HOME} push -u ${GH_URL} master"""
				echo STDOUT
				
				return
				STDOUT = bat label: "Cloning Repo ${GH_URL}",
				returnStdout: true,
				script:""" ${GIT_HOME} clone ${GH_URL} ."""
				echo STDOUT
				STDOUT = bat label: "Checking out branch ${env.BRANCH_NAME}",
				returnStdout: true,
				script:""" ${GIT_HOME} checkout ${env.BRANCH_NAME}"""
				echo STDOUT
				STDOUT = bat label: "Creating new Branch named PreProd${env.BUILD_NUMBER}",
				returnStdout: true,
				script:""" ${GIT_HOME} checkout -b Prod${env.BUILD_NUMBER}"""
				echo STDOUT
				STDOUT = bat label: "Pushing Branch PreProd${env.BUILD_NUMBER} to ${GH_URL}",
				returnStdout: true,
				script:""" ${GIT_HOME} push -u ${GH_URL} PreProd${env.BUILD_NUMBER}"""
				echo STDOUT
			}
			 if ((env.BRANCH_NAME =~ /develop/)){
                    		
                	        input(id: "Is this a Relase candidate?", message: "Relase to ..?", ok: 'Release')
				STDOUT = bat label: "Cloning Repo ${GH_URL}",
				returnStdout: true,
				script:""" ${GIT_HOME} clone ${GH_URL} ."""
				echo STDOUT
				STDOUT = bat label: "Checking out branch ${env.BRANCH_NAME}",
				returnStdout: true,
				script:""" ${GIT_HOME} checkout ${env.BRANCH_NAME}"""
				echo STDOUT
				STDOUT = bat label: "Creating new Branch named Release${env.BUILD_NUMBER}",
				returnStdout: true,
				script:""" ${GIT_HOME} checkout -b Release${env.BUILD_NUMBER}"""
				echo STDOUT
				STDOUT = bat label: "Pushing Branch Release${env.BUILD_NUMBER} to ${GH_URL}",
				returnStdout: true,
				script:""" ${GIT_HOME} push -u ${GH_URL} Release${env.BUILD_NUMBER}"""
				echo STDOUT
			}
				
                }
                
                
            }
        }
    }
}
