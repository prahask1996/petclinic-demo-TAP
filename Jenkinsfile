pipeline{
  environment{
    registry = "prahaskattimani/petclinic"
    registryCredential ='docker_hub_prahaskattimani'
    dockerImage = ''
  }
  agent any
  stages{
    stage('build'){
      steps{
        echo "Building Project"
        sh './mvnw package'
      }
    }
    stage('archive'){
      steps{
        echo "archiving Project"
        archiveArtifacts artifacts: '**/*jar', followSymlinks: false
      }
    }
    stage('build docker image'){
      steps{
        echo "Building docker image"
      }
    }
    stage('push docker image'){
      steps{
        echo "pushing docker image"
      }
    }
    stage('deploy to dev'){
      steps{
        echo "deployeing to dev environment"
      }
    }
  }
}
