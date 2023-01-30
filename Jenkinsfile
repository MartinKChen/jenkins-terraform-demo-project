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
      withCredentials([string(credentialsId: 'aws_access_key_id', variable: 'AWS_ACCESS_KEY_ID'), 
                       string(credentialsId: 'aws_secret_access_key', variable: 'AWS_SECRET_ACCESS_KEY')]) {
        steps {
          sh ('terraform apply -auto-approve')
        }
      }
    }
  }
}
