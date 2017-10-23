pipeline {
  agent any
  stages {
    stage('Checkout Code') {
      steps {
        dir('robotframework-lint') {
            git(url: 'https://github.com/boakley/robotframework-lint.git', branch: 'master')
        }
        dir('robotframework-hub') {
            git(url: 'https://github.com/boakley/robotframework-hub.git', branch: 'master')
        }
        sh '''
        echo 'hello, world'
        echo "pwd: `pwd`"
        ls -l
        '''
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