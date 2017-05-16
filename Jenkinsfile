pipeline {
  agent any
  stages {
    stage('Greeting') {
      steps {
        parallel(
          "Greeting": {
            echo 'Hello World DevOps!'
            
          },
          "Getting latest version": {
            git 'https://github.com/djimenezv/sampleapp.git'
            
          }
        )
      }
    }
    stage('Unit Testing') {
      steps {
        sh 'mvn clean test'
      }
    }
  }
}