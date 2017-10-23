pipeline {
  agent any
  stages {
    stage('Checkout Code') {
      steps {
        dir(path: 'robotframework-lint') {
          git(url: 'https://github.com/boakley/robotframework-lint.git', branch: 'master')
        }
        
        dir(path: 'robotframework-hub') {
          git(url: 'https://github.com/boakley/robotframework-hub.git', branch: 'master')
        }
        
        sh '''
        echo \'hello, world\'
        echo "pwd: `pwd`"
        ls -l
        '''
      }
    }
    stage('Unit Tests') {
      parallel {
        stage('books2read') {
          steps {
            sh 'echo "unit tests..."'
          }
        }
        stage('draft2digital') {
          steps {
            sh 'echo \'python manage.py test draft2digital\''
          }
        }
        stage('reporting') {
          steps {
            sh 'echo \'python manage.py test reporting\''
          }
        }
        stage('things2do') {
          steps {
            sh 'echo \'python manage.py test things2do\''
          }
        }
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
    stage('Final QA') {
      steps {
        input 'Hey! Yo! All systems go?'
      }
    }
    stage('Deploy to Staging') {
      steps {
        sh 'echo "deploying..."'
      }
    }
  }
}