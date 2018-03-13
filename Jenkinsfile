pipeline {
  agent {
    node {
      label 'Mint'
    }
    
  }
  stages {
    stage('Bring Up Grid') {
      steps {
        sh '''docker run -d -p 4444:4444 --name selenium-hub selenium/hub
docker run -d --link selenium-hub:hub selenium/node-chrome
docker run -d --link selenium-hub:hub selenium/node-firefox'''
      }
    }
    stage('Test') {
      parallel {
        stage('Test') {
          steps {
            sh 'docker run -e MODULE=order-module.xml -e BROWSER=firefox -e SELENIUM_HUB=selenium-hub vinsdocker/containertest:demo'
          }
        }
        stage('') {
          steps {
            sh 'docker run -e MODULE=order-module.xml -e BROWSER=chrome -e SELENIUM_HUB=selenium-hub vinsdocker/containertest:demo'
          }
        }
      }
    }
  }
}