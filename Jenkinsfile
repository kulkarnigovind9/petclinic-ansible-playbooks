node{
    
   stage('Clone Repository') {
        // Get some code from a GitHub repository
        git 'https://github.com/kulkarnigovind9/petclinic-ansible-playbooks.git'
   }
   
    stage('Update Image Tag'){
        echo params.IMAGE_TAG
        sh "sed -i 's/latest/$params.IMAGE_TAG/g' docker-compose.yml"
    }
    
    stage('deploy app'){
        ansiblePlaybook become: true, colorized: true, credentialsId: 'app-server-ssh-key', disableHostKeyChecking: true, inventory: 'dev-inventory', playbook: 'playbooks/appserver.yaml'
    }
    
}