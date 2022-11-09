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
		  
	  stage ("sonar-publish"){
            steps {
                withSonarQubeEnv("sonarqube") {
                echo "=========== Performing Sonar Scan ============"
                sh "${tool("scannerHome")}/bin/sonar-scanner"
            }
            }
        }
        
		  
 }
}
