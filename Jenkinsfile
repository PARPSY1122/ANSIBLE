pipeline{
    agent any
    tools{
        ansible 'ansible'
    }
    stages{
        stage('clean workspace'){
            steps{
                cleanWs()
            } 
        }
        stage('checkout scm'){
            steps{
                git branch: 'main' url:'https://github.com/PARPSY1122/ANSIBLE.git'

            }    
        }
        stage('trivy fs scan'){
            steps{
                sh "trivy fs . > trivyfs.txt"
            }
        }
        stage("ansible provision"){
            steps{
                sh "pip install --upgrade requests==2.20.1"
                ansiblePlaybook playbook: 'ec2.yaml'
            }
        }
    }
}
