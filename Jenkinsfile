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
            }
         }
        stage ('Code Quality scan'){
       withSonarQubeEnv('Sonarserver') {
       sh "${mvnHome}/bin/mvn -f pom.xml sonar:sonar"
      }
    }
  }
}

