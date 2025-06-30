pipeline {
    agent any
    stages {
        stage('CLone') {
            steps {
                echo 'cloning code from github'
                git branch: 'main', url: 'https://github.com/venudodla1/mindcircuit15.git'
            }
        
    }
    stage('Build') {
        steps {
            echo 'Building code'
            sh 'mvn clean install'
        }
    
    }
    stage('Deploy') {
            steps {
                echo 'Deploying into tomcat'
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'tomcat-id', path: '', url: 'http://ec2-44-201-126-243.compute-1.amazonaws.com:8080/')], contextPath: 'app', onFailure: false, war: '**/*.war'
            }
        }
    }
}
