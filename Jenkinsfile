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
        environment{
            BUILD_SERVER='ec2-user@172.31.11.111'
        }
        
        stage('Test') {
            agent any
            steps {
               script {
                    sshagent(['slave2']) {} 
                    echo 'Compile the code'
                    // echo "Compiling for ${params.Env} environment"
                    // sh "mvn compile"
                    sh "scp -o StrictHostKeyChecking=no server-script.sh ${BUILD_SERVER}:/home/ec2-user"
                    sh "ssh -o StrictHostKeyChecking=no ${BUILD_SERVER} 'bash /home/ec2-user/server-script.sh'"
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
