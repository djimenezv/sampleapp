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
        junit 'target/surefire-reports/*.xml'
      }
    }
    stage('Integration test') {
      steps {
        sh 'mvn verify -DskipUts'
        junit 'target/failsafe-reports/*.xml'
      }
    }
    stage('Code Analysis') {
      steps {
        sh 'mvn -DskipUTs checkstyle:checkstyle pmd:pmd findbugs:findbugs'
      }
    }
    stage('Package') {
      steps {
        sh 'mvn clean package -DskipTests'
      }
    }
  }
}