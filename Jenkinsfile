pipeline {
  agent {
    node {
      label 'Mint'
    }
    
  }
  stages {
    stage('Stage1') {
      parallel {
        stage('Stage1') {
          steps {
            sh 'docker run -e MODULE=search-module.xml -e BROWSER=firefox -e SELENIUM_HUB=selenium-hub vinsdocker/containertest:demo'
          }
        }
        stage('Stage 2') {
          steps {
            sh 'docker run -e MODULE=order-module.xml -e BROWSER=firefox -e SELENIUM_HUB=selenium-hub vinsdocker/containertest:demo'
          }
        }
      }
    }
  }
}