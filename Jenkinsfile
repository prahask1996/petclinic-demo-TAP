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
           docker.withRegistry( '', registryCredential){
            dockerImage.push()
            dockerImage.push('latest')
           }
        }
      }
    }
    stage('deploy to dev'){
      steps{
        echo "deployeing to dev environment" 
        sh "docker run -d --name=petclinic -p 8081:8080 prahaskattimani/petclinic"
      }
    }
  }
}
