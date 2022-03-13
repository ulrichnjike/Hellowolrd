pipeline {
  agent any
  tools {
     maven 'M2_HOME'  
  }
   environment {
    registry = "ulrichnjike/devop-code"
    registryCredential = 'DockerUserID'
  }
  stages {
    stage('build'){
      steps {
       sh 'mvn clean'
       sh 'mvn install'
       sh 'mvn package'
      }
    }
    stage('test'){
      steps {
       echo "test step"
       sh 'mvn test'
      }
    }    
    stage('Deploy'){
      steps {
       script {
        docker.build registry + ":$BUILD_NUMBER"
       }
      }
    }    
  }      
}
