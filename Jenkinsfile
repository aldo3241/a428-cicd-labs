pipeline{
    agent{
        docker{
            image 'node:16-buster-slim'
            args '-p 3000:3000'
        }
    }
    stages{
        stage('Build'){
            steps{
                sh 'npm install'
            }
        }
        stage('Test'){
            steps{
                sh './jenkins/scripts/test.sh'
            }
        }
        stage('Deploy'){
          steps{
            sh './jenkins/scripts/deliver.sh'
            dialog title: 'Application Started', message: 'Sudah selesai menggunakan React App? (React app akan Auto abort dalam 1 menit)'
            sleep 60
            sh './jenkins/scripts/kill.sh'
          }
        }
    }
}