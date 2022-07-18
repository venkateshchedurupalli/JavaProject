pipeline {
    agent any
	parameters{
       choice(name: 'VERSION', choices:['1.1.0','1.2.0','1.3.0'], description: '')
       booleanParam(name: 'executeTests', defaultValue: true, description: '')
     }
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

       //stage('Code Testing') {
		//	if(ENABLE_TESTING == "true"){
          //  steps {
            //   withSonarQubeEnv('sonar-9'){
              //   sh "mvn  sonar:sonar" 
				// }
                //}
		     //}
		  //else{
		   //echo "skipping testing";
		  //}
        //}
		
		stage('Advance') {
           when {
                expression{
                    params.executeTests
                }
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
