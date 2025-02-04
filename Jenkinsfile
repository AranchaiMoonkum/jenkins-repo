pipeline {
    agent any
    stages {      
        stage("Copy file to Docker server"){
            steps {
                sh "scp -r /var/lib/jenkins/workspace/test/* root@54.169.80.15:~/test"
            }
        }
        
        stage("Build Docker Image") {
            steps {
				ansiblePlaybook playbook: '/var/lib/jenkins/workspace/test/playbooks/build.yaml'
            }    
        } 
        
        stage("Create Docker Container") {
            steps {
				ansiblePlaybook playbook: '/var/lib/jenkins/workspace/test/playbooks/deploy.yaml'
            }    
        } 
    }
}
