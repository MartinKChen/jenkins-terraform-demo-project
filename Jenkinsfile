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
        sh ('TF_LOG=DEBUG terraform init')
      }
    }

    stage ("terraform apply") {
      steps {
        sh ('whoami')
        sh ('TF_LOG=DEBUG terraform apply -auto-approve')
      }
    }
  }
}
