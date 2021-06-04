pipeline {
  agent {
    node {
      label 'jk'
    }

  }
  stages {
    stage('build') {
      steps {
        dockerNode(image: 'node:6-alpine')
        sh 'npm install'
      }
    }

    stage('test') {
      steps {
        sh 'sh \'./jenkins/scripts/test.sh\''
      }
    }

    stage('Deliver') {
      steps {
        sh './jenkins/scripts/deliver.sh'
        echo 'Finished job'
        sh './jenkins/scripts/kill.sh'
      }
    }

  }
}