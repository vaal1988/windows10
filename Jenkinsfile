pipeline {
  agent {label 'gateway'}

  environment {
      TMPDIR                      = '/var/tmp/'
      PACKER_IMAGES_OUTPUT_DIR    = '/var/tmp/'
  }

  stages {

    // stage('PreCleanUP') {
    //   steps {
    //     sh 'vagrant box list | grep windows10 && vagrant box remove windows10 || exit 0'
    //     sh 'sudo rm -f /var/lib/libvirt/images/windows10_vagrant_box_image*'
    //     sh 'rm -rf /var/tmp/windows10/'
    //     sh 'rm -f /var/tmp/windows10.box'
    //   }
    // }

    stage('Source') {
      steps {
        git branch: 'main',
          url: 'https://github.com/vaal1988/windows10.git'
      }
    }

    stage('DownloadISO') {
      steps {
        sh 'ansible localhost -m get_url -a "url=https://tb.rg-adguard.net/dl.php?go=fb555f3a dest=./iso/Win10_21H1_English_x64.iso"'
      }
    }

    // stage('Build') {
    //   steps {
    //     sh 'packer build -only="qemu" windows10.json'
    //   }
    // }

    stage('Test') {
      steps {
        sh 'vagrant box add windows10 /var/tmp/windows10.box --provider libvirt'
        sh 'vagrant up'
      }
    }

    stage('CleanUP') {
      steps {
        sh 'vagrant destroy --force'
        sh 'vagrant box remove windows10'
        sh 'rm -rf /var/tmp/windows10/'
        sh 'rm -f ./iso/Win10_21H1_English_x64.iso'
        sh 'sudo rm -f /var/lib/libvirt/images/windows10_vagrant_box_image*'
      }
    }

  }
}
