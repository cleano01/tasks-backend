pipeline{
    agent any
    stages {
        stage ('Inicio'){
            steps {
                sh 'echo inicio'
            }
        }
        stage('Meio'){
            steps{
                sh 'echo meio'
            }
        }
        stage('Fim'){
            steps{
                sleep(5)
                sh 'echo fim!'
            }
        }
    }
}