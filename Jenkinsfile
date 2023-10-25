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
                withSonarQubeEnv('sonar-server') {
                    tool name: 'jdk17', type: 'jdk'
                    sh '''$SCANNER_HOME/bin/sonar-scanner -Dsonar.projectName=Netflix \
                    -Dsonar.projectKey=Netflix -Dsonar.host.url=http://52.23.47.49:9000 \
                    -Dsonar.token=sqp_a50e49176f25b22a3ce539bcad05bdc489547098'''
                }
            }
        }
    }
}