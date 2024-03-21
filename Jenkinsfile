pipeline {
   environment {
        registry = "venkataravisridhardevarakonda/survey"
        registryCredential = 'dockerhub_credential'
        TIMESTAMP = new Date().format("yyyyMMdd_HHmmss")
        KUBECONFIG = '/home/ubuntu/.kube' // Path to Kubernetes configuration file
    }
   agent any

   stages {
      stage('Build') {
         steps {
            script{
               sh 'pwd'
               sh 'rm -rf *.war'
               sh 'ls -l'
               sh 'jar -cvf Assign1Part2.war -C src/main/webapp/ .'
               docker.withRegistry('',registryCredential){
                  def customImage = docker.build("${registry}:${env.TIMESTAMP}")
               }
            }
         }
      }

      stage('Push Image to Dockerhub') {
         steps {
            script{
               docker.withRegistry('',registryCredential){
                  sh "docker push ${registry}:${env.TIMESTAMP}"
               }
            }
         }
      }

      stage('Deploying to Rancher on a single node, which is configured to have three replicas deployed.') {
         steps {
            script{
               withKubeConfig([credentialsId: 'kubeconfig_credentials', serverUrl: 'https://ec2-18-233-14-73.compute-1.amazonaws.com/k8s/clusters/c-m-xnwhb6hl']) {
                   sh "kubectl set image deployment/survey container-0=${registry}:${env.TIMESTAMP}"
               }
            }
         }
      }

      stage('Deploying to Rancher utilizing a Load Balancer as a service.') {
         steps {
            script{
               withKubeConfig([credentialsId: 'kubeconfig_credentials', serverUrl: 'https://ec2-18-233-14-73.compute-1.amazonaws.com/k8s/clusters/c-m-xnwhb6hl']) {
                   sh "kubectl set image deployment/survey-lb container-0=${registry}:${env.TIMESTAMP}"
               }
            }
         }
      }
   }
}
