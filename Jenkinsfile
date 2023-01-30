pipeline {
  agent any

  stages {
    stage('checkout') {
      steps {
        checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/MartinKChen/jenkins-terraform-demo-project']]])
      }
    }

    stage ("terraform init") {
      steps {
        sh ('terraform init')
      }
    }

    stage ("terraform apply") {
      steps {
        sh ('ls -ltra')
        sh ('terraform apply –auto-approve')
      }
    }
  }
}
