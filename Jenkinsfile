pipeline {
    agent {
        label 'AGENT1'
    }
    options {
        ansiColor('xterm')
    }
    stages{
        stage('Build') {
            steps {
                echo 'Building...'
            }
        }
        stage('Test'){
            steps{
                echo 'Testing...'
            }
        }
        stage('Deploy'){
            steps{
                echo 'Deploying...'
            }
        }
    }
}