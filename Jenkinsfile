pipeline {
  agent {label 'qemu'}

  environment {
      TMPDIR                      = '/var/tmp/'
      PACKER_IMAGES_OUTPUT_DIR    = '/var/tmp/'
  }

  stages {
    stage('Source') {
      steps {
        git branch: 'main',
          url: 'https://github.com/vaal1988/windows10.git'
        sh 'ls -1'
      }
    }
    stage('Packer') {
      steps {
        sh 'env'
      }
    }
  }
}