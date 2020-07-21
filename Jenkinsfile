pipeline{
    agent any
    stages {
        stage ('Build Backend'){
            steps {
                sh 'mvn clean package -DskipTest=true'
            }
        } 
        stage ('Unit Tests'){
            steps {
                sh 'mvn test'
            }
        }
        stage ('Deploy Backend'){
            steps {
                deploy adapters: [tomcat8(credentialsId: 'tomcatLogin', path: '', url: 'http://localhost:8001/')], contextPath: 'tasks-backend', war: 'target/tasks-backend.war'            }
        }
        stage ('Api Tests'){
            steps {
                git credentialsId: 'github_login', url: 'https://github.com/wcaquino/tasks-api-test'
                sh 'mvn test'
            }
        }
    }
}

