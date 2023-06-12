  pipeline {
  agent any

  stages {
    stage('Build Artifact - Maven') {
      steps {
        sh "mvn clean package -DskipTests=true"
        archive 'target/*.jar'
      }
    }

    stage("Test"){
            steps{
                // mvn test
                sh "mvn test"
      }
    }
    stage ('CODE ANALYSIS WITH CHECKSTYLE'){
            steps {
                sh 'mvn checkstyle:checkstyle'
            }
            post {
                success {
                    echo 'Generated Analysis Result'
               }    
            } stage('SonarQube - SAST') {
      steps {
        sh "mvn sonar:sonar -Dsonar.projectKey=numeric-application -Dsonar.host.url=http://localhost:9000 -Dsonar.login=0925129cf435c63164d3e63c9f9d88ea9f9d7f05"
         }
      }           
   }
}
