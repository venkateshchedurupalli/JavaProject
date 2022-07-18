pipeline {
    agent any
    tools {
      maven 'M2_HOME'
      jdk 'JAVA_HOME'
    }

  

    stages {
            
          stage('Checkout'){
            steps{
             git 'https://github.com/venkateshchedurupalli/JavaProject.git'
            }
		}


        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

       stage('Code Testing') {
	       if(ENABLE_TESTING == "true"){
            steps {
               withSonarQubeEnv('sonar-9'){
                 sh "mvn  sonar:sonar" 
				 }
                }
		     }
		  else{
		   echo "skipping testing";
		  }
        }
  
        
           stage('Test'){
            steps {
                echo 'Hello world!' 
                sh 'java -version'
                echo "Test"
            }
                }
        
         
        stage('Deploy') {
            steps {
                echo 'Deploying the application....'
            }
        }
    }
}
