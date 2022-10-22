pipeline {
    agent any
    stages {
        stage('SCM'){
            steps {
                git 'https://github.com/Hrudaya-github/game-of-life.git'
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
