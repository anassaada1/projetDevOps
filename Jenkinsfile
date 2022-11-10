pipeline {
      agent any
	 tools {
    	maven 'M2_HOME'
    }
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
		  
		stage("SonarQube Analysis") {
            steps {
              withSonarQubeEnv('SonarQube') {
                sh 'mvn clean -DskipTests package sonar:sonar'
              }
            }
          }
        
		  
 }
}
