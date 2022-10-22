pipeline {
    agent any
    stages {
        stage('SCM'){
            steps {
                git 'https://github.com/Hrudaya-github/game-of-life.git'
            }
        }
        stage('Unit Testing'){
            steps {
                script {
                    sh 'mvn test'
                }
                
            }
        }
        stage('Integration Testing'){
            steps {
                script {
                    sh 'mvn verify -DskipUnitTests'
                }
                
            }
        }
        stage('Maven Build'){
            steps {
                script {
                    sh 'mvn clean install'
                }
                
            }
        }
        stage('Build & Sonarqube Analysis'){
            steps {
                script {
                    withSonarQubeEnv('sonar-server') {
                     sh script: 'mvn clean package sonar:sonar'
                    }
                }                
            }
        }
    }
}
