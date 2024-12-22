pipeline {
  agent any
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  stages {
    stage('hello') {
      W
      steps {
       echo 'Hello'
      }
    }
    stage('cat README') {
      when {
        branch "fix-*"
      }
      steps {
        sh '''
        cat README.md
        '''
      }
    }
  }
  post {
    always {
        junit(
          allowEmptyResults: true, 
          testResults: '**/build/test-results/test/*.xml'
        )
    }
  }
}