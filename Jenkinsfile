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
          git branch: 'main',
            credentialsId: 'github',
            url: 'https://github.com/humayun-alam/jenkins-ansible-deploy.git'
           }
          }
     stage("Maven Build"){
       steps{
            sh "mvn clean package"
//            sh "mv target/*.war target/myweb.war"
             }
            }
     stage("Ansible Deploy"){
       steps{
         sshagent (['ansible-server']) {
                ansiblePlaybook(
                    credentialsId: 'ansible-server',
                    inventory: 'inventory.yml',
                    installation: 'ansible-tool',
                    limit: 'kvm-tomcat',
                    playbook: 'playbook.yml',
                   
                )
            }
            }
          }
        }
        
    }
