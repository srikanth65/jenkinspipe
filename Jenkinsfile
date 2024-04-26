pipeline {
    agent {
        label 'AGENT1'
    }
    options {
        ansiColor('xterm')
    }
    parameters {
        choice(name: 'action', choices: ['apply', 'destroy'], description: 'Pick something')
    }
    stages{
        stage('Init') {
            steps {
                echo 'terraform initializing...'
                sh """
                terraform init
                """
            }
        }
        stage('plan'){
            steps{
                echo 'Terraform plan applying...'
                sh """
                terraform plan
                """
            }
        }
        stage('Deploy'){
            when { 
                expression {  
                    params.action == 'apply'
                    } 
                }
            input {
                message "Should we continue?"
                ok "Yes, we should."
            }
            steps{
                echo 'Terraform Deploy applying...'
                sh """
                terraform apply --auto-approve
                """
            }
        }
        stage('Destroy'){
            when { 
                expression {  
                    params.action == 'destroy'
                    } 
                }
            input {
                message "Should we continue?"
                ok "Yes, we should."
            }
            steps{
                echo 'Terraform destroying applying...'
                sh """
                terraform destroy --auto-approve
                """
            }
        }
    }
    post { 
        always { 
            echo 'I will always say Hello again!!'
        }
        failure { 
            echo 'this runs when pipeline is failed, used generally to send some alerts'
        }
        success{
            echo 'I will say Hello when pipeline is success'
        }
    }
}