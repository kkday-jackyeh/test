pipeline {
  agent any

  stages {
    stage('Test Timeout') {
      steps {
        timeout(time: 2, unit: 'MINUTES') {
          sh -c 'sh delay.sh'
        }
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