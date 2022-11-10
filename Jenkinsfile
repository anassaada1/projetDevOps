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
		  
		 stage('SonarQube analysis') {
		        steps {
		        withSonarQubeEnv(installationName: 'sq1') {
                      sh './mvnw clean org.sonarsource.scanner.maven:sonar-maven-plugin:3.9.0.2155:sonar'
	                  }
	                }
	            }
        
		  
 }
}
