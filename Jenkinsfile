pipeline {
  agent any

  options {
    timeout(time: 3, unit: 'MINUTES') 
  }

  stages {
    stage('Test Timeout 1') {
      steps {
        sh 'sh delay.sh'
      }
    }

    stage('Test Timeout 2') {
      steps {
        sh 'sh delay.sh'
      }
    }
  }

  post {
    success {
      slackSend channel: '#it-devops-test',
        color: 'good',
        message: "*${currentBuild.currentResult}:* Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}\n More info at: ${env.BUILD_URL}"
    }
    failure {
      slackSend channel: '#it-devops-test',
        color: 'danger',
        message: "*${currentBuild.currentResult}:* Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}\n More info at: ${env.BUILD_URL}"
    }
  }
}