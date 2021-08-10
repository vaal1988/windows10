pipeline {
  agent {label 'qemu'}

  stages {
    stage('Source') {
      steps {
        git 'https://github.com/vaal1988/windows10.git'
        sh 'ls -lA .'
      }
    }
  }
}