pipeline {
    agent any 
    stages {
        stage('Clone the repo') {
            steps {
                echo 'clone the repo'
                bat 'rm -fr html'
                bat 'git clone https://github.com/dmccuk/html.git'
            }
        }
        stage('push repo to remote host') {
            steps {
                echo 'connect to remote host and pull down the latest version'
                bat 'ssh -i ~/working.pem ec2-user@192.168.1.220 sudo git -C /var/www/html pull'
            }
        }
        stage('Check website is up') {
            steps {
                echo 'Check website is up'
                bt 'curl -Is 192.168.1.220 | head -n 1'
            }
        }
    }
}
