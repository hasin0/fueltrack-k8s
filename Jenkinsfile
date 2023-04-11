pipeline {

  environment {
    dockerimagename = "hasino2258/fueltrack:2.1"
    dockerImage = ""
  }

  agent any

  stages {

    stage('Checkout Source') {
      steps {
        git 'https://github.com/hasin0/fueltrack.git'
      }
    }

    

    stage('Build image') {
      steps{
        script {
               
        //   sh 'composer install --ignore-platform-req=ext-gd'

          dockerImage = docker.build dockerimagename
        }
      }
    }

    stage('Pushing Image') {
      environment {
               registryCredential = 'docker-hub cred'
           }
      steps{
        script {
        docker.build DOCKER_IMAGE_NAME
          docker.withRegistry("https://registry.hub.docker.com", registryCredential) {
            docker.push DOCKER_IMAGE_NAME
          }
        }
      }
    }

    stage('Deploying Laravel container to Kubernetes') {
      steps {
        script {
          kubernetesDeploy(configs: "fueltrack-depl.yaml", "fueltrack-service")
        }
      }
    }

  }

}




























// pipeline {
//   environment {
//     DOCKER_IMAGE_NAME = "my-docker-hub-username/my-docker-image-name"
//     KUBECONFIG = credentials("kubeconfig-credential-id")
//   }
  
//   agent {
//     label "my-agent-label"
//   }
  
//   stages {
//     stage("Checkout Source") {
//       steps {
//         git url: "https://github.com/my-github-username/my-github-repo.git"
//       }
//     }
    
//     stage("Build and Push Docker Image") {
//       steps {
//         script {
//           docker.build DOCKER_IMAGE_NAME
//           docker.withRegistry("https://registry.hub.docker.com", "docker-hub-credentials-id") {
//             docker.push DOCKER_IMAGE_NAME
//           }
//         }
//       }
//     }
    
//     stage("Deploy to Kubernetes") {
//       steps {
//         script {
//           kubernetesDeploy(
//             kubeconfigId: "kubeconfig-credential-id",
//             configs: [
//               file(credentials("kubernetes-deployment-yaml-credential-id")),
//               file(credentials("kubernetes-service-yaml-credential-id"))
//             ],
//             enableConfigSubstitution: true
//           )
//         }
//       }
//     }
//   }
// }
