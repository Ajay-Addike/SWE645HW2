pipeline {
   environment {
        registry = "venkataravisridhardevarakonda/survey"
        registryCredential = 'dockerhub_credential'
        TIMESTAMP = new Date().format("yyyyMMdd_HHmmss")
    }
   agent any

   stages {
      stage('Build') {
         steps {
            script{
               sh 'pwd'
               sh 'rm -rf *.war'
               sh 'ls -l'
               sh 'jar -cvf SWE645HW1.war -C WebContent/ .'
               docker.withRegistry('',registryCredential){
                  def customImage = docker.build("venkataravisridhardevarakonda/survey:${env.TIMESTAMP}")
               }
            }
         }
      }

      stage('Push Image to Dockerhub') {
         steps {
            script{
               docker.withRegistry('',registryCredential){
                  sh "docker push venkataravisridhardevarakonda/survey:${env.TIMESTAMP}"
               }
            }
         }
      }

      stage('Deploying to Rancher to single node(deployed in 3 replicas)') {
         steps {
            script{
               sh "kubectl set image deployment/survey container-0=venkataravisridhardevarakonda/survey:${env.TIMESTAMP}"
            }
         }
      }

      stage('Deploying to Rancher using Load Balancer as a service') {
         steps {
            script{
               sh "kubectl set image deployment/survey-lb container-0=venkataravisridhardevarakonda/survey:${env.TIMESTAMP}"
            }
         }
      }
   }
}
