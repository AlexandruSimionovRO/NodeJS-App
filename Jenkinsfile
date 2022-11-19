pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                script {
                    def dockerCmd = 'docker run -p 7878:3080 -d alexsv1/nodejsapp-itschool:latest'
                    sshagent(['AWS-EC2-KEY']) {
                        sh "ssh -o StrictHostKeyChecking=no ec2-user@3.72.254.122 ${dockerCmd}"
                    }
                }
            }
        }
    }
}


