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
            steps {
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
