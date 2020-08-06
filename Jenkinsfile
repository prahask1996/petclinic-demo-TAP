pipeline{
  agent any
  stages{
    stage('build'){
      steps{
        echo "Building Project"
      }
    }
    stage('archive'){
      steps{
        echo "archiving Project"
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
