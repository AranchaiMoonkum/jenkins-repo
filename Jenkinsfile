pipeline {
    agent any
    stages {      
        stage("Copy file to Docker server"){
            steps {
                sh "scp -r /var/lib/jenkins/workspace/team24-work/* root@13.212.94.247:~/team24-carvilla"
            }
        }
        
        stage("Build Docker Image") {
            steps {
				ansiblePlaybook playbook: '/var/lib/jenkins/workspace/team24-work/playbooks/build.yaml'
            }    
        } 
        
        stage("Create Docker Container") {
            steps {
				ansiblePlaybook playbook: '/var/lib/jenkins/workspace/team24-work/playbooks/deploy.yaml'
            }    
        } 
    }
}
