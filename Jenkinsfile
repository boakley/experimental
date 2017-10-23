pipeline {
  agent any
//    node {
//      label 'Whatever'
//    }
    
  }
  stages {
    stage('Build') {
      steps {
        git(url: 'https://github.com/boakley/robotframework-lint.git', branch: 'master', changelog: true)
        git(url: 'https://github.com/boakley/robotframework-hub.git', branch: 'master')
      }
    }
    stage('Unit Tests') {
      steps {
        sh 'echo "unit tests..."'
      }
    }
    stage('Robot Tests') {
      parallel {
        stage('Chrome') {
          steps {
            sh 'echo \'chrome tests...\''
          }
        }
        stage('Firefox Tests') {
          steps {
            sh 'echo \'firefox tests...\''
          }
        }
      }
    }
    stage('Deploy to Staging?') {
      steps {
        sh 'echo \'deploying to staging\''
      }
    }
  }
}
