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
        script{
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }
    stage('push docker image'){
      steps{
        echo "pushing docker image"
         script{
           withDockerRegistry( '', registryCredential){
            dockerImage.push()
           }
        }
      }
    }
    stage('deploy to dev'){
      steps{
        echo "deployeing to dev environment"
      }
    }
  }
}
