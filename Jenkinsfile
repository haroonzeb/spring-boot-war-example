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
  }
}

