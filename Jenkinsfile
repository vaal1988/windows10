pipeline {
  agent {label 'qemu'}

  stages {
    stage('Source') {
      steps {
        git branch: 'main',
          url: 'https://github.com/vaal1988/windows10.git'
        sh 'ls -1'
      }
    }
  }
}