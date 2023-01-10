pipeline {
    agent any
    environment {
        AWS_ACCOUNT_ID="999134889162"
        AWS_DEFAULT_REGION="us-east-1"
        IMAGE_REPO_NAME="node-js-app-production-ecr"
        IMAGE_TAG="v1"
        REPOSITORY_URI = "999134889162.dkr.ecr.us-east-1.amazonaws.com/node-js-app-production-ecr"
    }
   
    stages {
        
         stage('Logging into AWS ECR') {
            steps {
                script {
                sh """aws ecr get-login-password --region ${AWS_DEFAULT_REGION} | docker login --username AWS --password-stdin ${AWS_ACCOUNT_ID}.dkr.ecr.${AWS_DEFAULT_REGION}.amazonaws.com"""
                }
                 
            }
        }
        
  
    // Building Docker images
    stage('Building image') {
      steps{
        script {
          sh """cd /var/lib/jenkins/workspace/backend-app/frontend/ | dockerImage = docker.build ${IMAGE_REPO_NAME}:${IMAGE_TAG}"""
          
        }
      }
    }
   
    // Uploading Docker images into AWS ECR
    stage('Pushing to ECR') {
     steps{  
         script {
                sh """docker tag ${IMAGE_REPO_NAME}:${IMAGE_TAG} ${REPOSITORY_URI}:$IMAGE_TAG"""
                sh """docker push ${AWS_ACCOUNT_ID}.dkr.ecr.${AWS_DEFAULT_REGION}.amazonaws.com/${IMAGE_REPO_NAME}:${IMAGE_TAG}"""
         }
        }
      }
    }
}
