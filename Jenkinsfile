pipeline {
    agent any
     
    stages {
        stage("Test"){
            steps{
                // mvn test
                sh "mvn test"
                
            }
            
        }
        stage("Build"){
            steps{
                sh "mvn package"
                
            }
            
        }
 stage('Docker Build and Push') {
      steps {

          sh 'docker build -t siddharth67/numeric .'
        }
     
    } 
}         
