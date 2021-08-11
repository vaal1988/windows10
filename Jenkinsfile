pipeline {
  agent {label 'homepc'}

  environment {
      TMPDIR                      = '/var/tmp/'
      PACKER_IMAGES_OUTPUT_DIR    = '/var/tmp/'
  }

  stages {
    
    stage('Source') {
      steps {
        git branch: 'main',
          url: 'https://github.com/vaal1988/windows10.git'
      }
    }
    
    // stage('DownloadISO') {
    //   steps {
    //     sh 'wget -qO ./iso/Win10_21H1_English_x64.iso https://tb.rg-adguard.net/dl.php?go=fb555f3a'
    //   }
    // }
    
    stage('Build') {
      steps {
        sh 'packer build -only="qemu" windows10.json'
      }
    }

    stage('Test') {
      steps {
        sh 'sudo mv --force /var/tmp/windows10/windows10 /var/lib/libvirt/images/windows10.qcow2'
      }
    }

    stage('CleanUP') {
      steps {
        sh 'rm -rf /var/tmp/windows10/'
        sh 'rm -f ./iso/Win10_21H1_English_x64.iso'
      }
    }

  }
}