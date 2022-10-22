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
                sh 'mvn test'
            }
        }
        stage('Integration Testing'){
            steps {
                sh 'mvn verify -DskipUnitTests'
            }
        }
        stage('Maven Build'){
            steps {
                sh 'mvn clean install'
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
