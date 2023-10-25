pipeline {
    agent any
    tools {
        jdk 'jdk17'
        nodejs 'node16'
    }
    environment {
        SCANNER_HOME = tool 'sonar-scanner'
        JAVA_HOME = '/usr/lib/jvm/java-17-openjdk-amd64'
    }
    stages {
        stage('clean workspace') {
            steps {
                cleanWs()
            }
        }
        stage('Git Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Shadab-inzu/DevSecOps-Project.git'
            }
        }
       
        stage("Sonarqube Analysis") {
            steps {
                withCredentials([string(credentialsId: 'sonar-token', variable: 'sonar')]) {
     sh '''$SCANNER_HOME/bin/sonar-scanner \
                        -Dsonar.projectKey=Netfilx \
                        -Dsonar.sources=. \
                        -Dsonar.host.url=http://52.23.47.49:9000 \
                        -Dsonar.token=sqp_a50e49176f25b22a3ce539bcad05bdc489547098'''
                    }
               
                }
            }
        }
    }
}