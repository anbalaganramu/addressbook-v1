pipeline {
    agent any
    stages {
        stage('Compile') {
            agent {label 'newslave'}
            steps {
                script{
                    echo 'Compile Job'
                    sh "mkdir devOps"
                }
                
            }
        }
             
        stage('Test') {
            agent any
            steps {
               script {
                    sshagent(['slave2']) {} 
                    echo 'Compile the code'
                    // echo "Compiling for ${params.Env} environment"
                    // sh "mvn compile"
                    sh "scp -o StrictHostKeyChecking=no server-script.sh ec2-user@172.31.11.111:/home/ec2-user"
                    sh "ssh -o StrictHostKeyChecking=no ec2-user@172.31.11.111 'bash /home/ec2-user/server-script.sh'"
                }
                echo 'Test Job'
            }
        }
        stage('Review') {
            steps {
                echo 'Review Job'
            }
        }
        stage('Package') {
            steps {
                echo 'Package Job'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploy Job'
            }
        }
    }
}
