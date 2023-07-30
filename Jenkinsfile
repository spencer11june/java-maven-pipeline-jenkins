pipeline {
    agent {
    label 'Slave'    
    }
tools {
        maven 'M2_HOME'
    }
    stages{
        stage('checkout the project'){
            steps{
                git branch: 'main', url: 'https://github.com/spencer11june/java-maven-pipeline-jenkins.git'
                
            }
        }
        stage('Build the package'){
            steps{
                sh 'mvn clean package'
            }
        }
        stage('Deploying') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'df8afbcc-8db0-45ed-8af8-6d69ef0e0953', path: '', url: 'http://65.2.143.254:8081')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
