pipeline {
      agent any

          stages {


	        stage('Checkout GIT ') {
                 steps {
                    echo 'Pulliing ...';
		            git branch: 'anas', credentialsId: 'jenkins-git', url: 'https://github.com/anassaada1/projetDevOps.git'
                        }
                 }
		  
		   stage('Cleaning the project') {
                 steps{
                    sh "mvn -B -DskipTests clean  "
                    }
                }
		  
		  stage('Testing Maven ') {
                 steps {
                    sh 'mvn -version'
                        }
                 }
		stage("SonarQube") {
    		steps {
				echo "\033[34m*********Stage SonarQube Started*********\033[0m";
	        	withSonarQubeEnv('My SonarQube Server') {
				sh 'mvn clean -DskipTests package sonar:sonar'
				echo "\033[42m\033[97m*********SonarQube analysis finished with SUCCESS *********\033[0m"
            	}
        	}
		}
        
		  
 }
}
