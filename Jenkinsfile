pipeline {


  agent any

  stages {

    stage('Checkout Source') {
      steps {
        git 'https://github.com/ChaaraouiMohammed/wordpress.git'
      }
    }

    stage('Build image') {
      steps{
        script {
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }

    stage('Push Image') {
      steps{
        script {
          docker.withRegistry( "" ) {
            dockerImage.push()
          }
        }
      }
    }

    stage('Deploy App') {
      steps {
        script {
          kubernetesDeploy(configs: "mysql-deployment.yaml", kubeconfigId: "mykubeconfig")
        }
      }
    }

  }

}
