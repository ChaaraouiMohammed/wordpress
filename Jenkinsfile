pipeline {


  agent any

  stages {

    stage('Deploy App') {
      steps {
        script {
          kubernetesDeploy(configs: "mysql-deployment.yaml", kubeconfigId: "mykubeconfig")
        }
      }
    }

  }

}
