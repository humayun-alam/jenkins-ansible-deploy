pipeline{
  agent {
    label "test-server"
  }

  tools {
    maven "maven"
  }
  stages{
    stage("Git Checkout"){
      steps{
          git branch: 'branch01',
            credentialsId: 'github',
            url: 'https://github.com/humayun-alam/jenkins-ansible-deploy.git'
           }
          }
     stage("Maven Build"){
       steps{
            sh "mvn clean package"
             }
            }
     stage("Ansible Deploy"){
         steps {
             ansiblePlaybook become: true, credentialsId: 'ansible-server', disableHostKeyChecking: true, playbook: 'playbook.yml', inventory: 'inventory.yml'
           }
        }
    }
}
