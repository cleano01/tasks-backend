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
              deploy adapters: [tomcat8(credentialsId: 'tomcatLogin', path: '', url: 'http://localhost:8001/')], contextPath: 'tasks-backend', war: 'target/tasks-backend.war'            
            } 
        }
        //stage ('Api Test') {
        //  steps {
        //    dir('api-test') {
        //      git credentialsId: 'github_login', url: 'https://github.com/cleano01/tasks-api-test'
        //      sh 'mvn test'
        //    }
        //  }
        //}
        stage ('Deploy Frontend'){
            steps {
              dir('frontend'){
                git credentialsId: 'github_login', url: 'https://github.com/cleano01/tasks-frontend'
                sh 'mvn clean package'
                deploy adapters: [tomcat8(credentialsId: 'tomcatLogin', path: '', url: 'http://localhost:8001/')], contextPath: 'tasks', war: 'target/tasks.war'            
              }
            } 
        }      
    }
}