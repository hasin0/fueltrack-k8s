node {
    def app

    stage('Clone repository') {
      

        checkout scm
    }

    stage('Update GIT') {
            script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    withCredentials([usernamePassword(credentialsId: 'gitHub', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                        def encodedPassword = URLEncoder.encode("$GIT_PASSWORD",'UTF-8')
                        sh "git config user.email hasino2258@gmail.com"
                        sh "git config user.name hasin0"
                        sh "git switch master"
                        sh "cat fueltrack-depl.yaml"
                        sh "sed -i 's+hasino2258/fueltrack.*+hasino2258/fueltrack:${DOCKERTAG}+g' fueltrack-depl.yaml"
                        sh "cat fueltrack-depl.yaml"
                        sh "git add ."
                        sh "git commit -m 'Done by Jenkins Job changemanifest: ${env.BUILD_NUMBER}'"
                        // sh "git push https://github.com/hasin0/fueltrack-k8s.git HEAD:main"


                        sh "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/${GIT_USERNAME}/fueltrack-k8s.git HEAD:main"
      }
    }
  }
}
}





















// pipeline {
//   environment {
//     dockerimagename = "hasino2258/fueltrack:latest"
//     dockerImage = ""
//   }
//   agent any
//   stages {
//     stage('Checkout Source') {
//       steps {
//         git 'https://github.com/hasin0/fueltrack-k8s.git'
//       }
//     }
//     // stage('Add Jenkins user to Docker group') {
//     //   steps {
//     //     sh 'sudo usermod -aG docker jenkins'
//     //   }
//     }
//     stage('Build image') {
//       steps{
//         script {
//           dockerImage = docker.build dockerimagename
//         }
//       }
//     }
//     stage('Pushing Image') {
//       environment {
//         registryCredential = 'docker-cred'
//       }
//       steps{
//         script {
//           docker.withRegistry('https://registry.hub.docker.com', registryCredential) {
//             dockerImage.push("latest")
//           }
//         }
//       }
//     }
//     stage('Deploying App to Kubernetes') {
//       steps {
//         script {
//           kubernetesDeploy(configs: "fueltrack-depl.yaml", serviceName: "fueltrack-service")
//         }
//       }
//     }
//   }
// }














// pipeline {
//   environment {
//     dockerimagename = "hasino2258/fueltrack:2.1"
//     dockerImage = ""
//   }
//   agent any
//   stages {
//     stage('Install Docker') {
//       steps {
//         script {
//           dockerTool = dockerTool installationName: 'default'
//           sh "${dockerTool}/bin/docker info"
//         }
//       }
//     }
//     stage('Checkout Source') {
//       steps {
//         git 'https://github.com/hasin0/fueltrack-k8s.git'
//       }
//     }
//     stage('Build image') {
//       steps {
//         script {
//           dockerImage = docker.build dockerimagename
//         }
//       }
//     }
//     stage('Pushing Image') {
//       environment {
//         registryCredential = 'docker-cred'
//       }
//       steps {
//         script {
//           docker.build dockerimagename
//           docker.withRegistry("https://registry.hub.docker.com", registryCredential) {
//             docker.push dockerimagename
//           }
//         }
//       }
//     }
//     stage('Deploying Laravel container to Kubernetes') {
//       steps {
//         script {
//           kubernetesDeploy(configs: "fueltrack-depl.yaml", serviceName: "fueltrack-service")
//         }
//       }
//     }
//   }
// }
























// pipeline {

//   environment {
//     dockerimagename = "hasino2258/fueltrack:2.1"
//     dockerImage = ""
//   }

//   agent any

//   stages {
//     stage('Install Docker')
//      {
//       steps {
//         sh '''
//           # Add Docker repository
//           curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
//           sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

//           # Update package index
//           sudo apt-get update

//           # Install Docker
//           sudo apt-get install docker-ce

//           # Add Jenkins user to docker group
//           sudo usermod -aG docker jenkins

//           # Restart Docker service
//           sudo systemctl restart docker
//         '''
//       }
//     }

//     stage('Checkout Source') {
//       steps {
//         git 'https://github.com/hasin0/fueltrack-k8s.git'
//       }
//     }

//     stage('Build image') {
//       steps {
//         script {
//           dockerImage = docker.build dockerimagename
//         }
//       }
//     }

//     stage('Pushing Image') {
//       environment {
//         registryCredential = 'docker-cred'
//       }
//       steps {
//         script {
//           docker.build dockerimagename
//           docker.withRegistry("https://registry.hub.docker.com", registryCredential) {
//             docker.push dockerimagename
//           }
//         }
//       }
//     }

//     stage('Deploying Laravel container to Kubernetes') {
//       steps {
//         script {
//           kubernetesDeploy(configs: "fueltrack-depl.yaml", "fueltrack-service")
//         }
//       }
//     }
//   }
// }
























// pipeline {

//   environment {
//     dockerimagename = "hasino2258/fueltrack:2.1"
//     dockerImage = ""
//   }

//   agent any



//   stages {
//     stage('Install Docker') {
//       steps {
//         sh '''
//           # Add Docker repository
//           curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
//           sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

//           # Update package index
//           sudo apt-get update

//           # Install Docker
//           sudo apt-get install docker-ce

//           # Add Jenkins user to docker group
//           sudo usermod -aG docker jenkins

//           # Restart Docker service
//           sudo systemctl restart docker
//         '''
//       }
//     }

//     // Add other stages as needed
//   }

//   stages {

//     stage('Checkout Source') {
//       steps {
//         git 'https://github.com/hasin0/fueltrack-k8s.git'
//       }
//     }

    

//     stage('Build image') {
//       steps{
//         script {
               
//         //   sh 'composer install --ignore-platform-req=ext-gd'

//           dockerImage = docker.build dockerimagename
//         }
//       }
//     }

//     stage('Pushing Image') {
//       environment {
//                registryCredential = 'docker-hub cred'
//            }
//       steps{
//         script {
//         docker.build DOCKER_IMAGE_NAME
//           docker.withRegistry("https://registry.hub.docker.com", registryCredential) {
//             docker.push DOCKER_IMAGE_NAME
//           }
//         }
//       }
//     }

//     stage('Deploying Laravel container to Kubernetes') {
//       steps {
//         script {
//           kubernetesDeploy(configs: "fueltrack-depl.yaml", "fueltrack-service")
//         }
//       }
//     }

//   }

// }




























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
