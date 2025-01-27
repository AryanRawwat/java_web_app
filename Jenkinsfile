pipeline {
    agent any

        tools {
        maven 'Maven 3'  // 
       }

    stages {
         stage('git clone') {
            steps {
              git branch: 'main', credentialsId: 'jenkins-github', url: 'https://github.com/AryanRawwat/java_web_app.git'
            }
        }

          stage('build') {
            steps {
               sh 'mvn clean install'
            }
        }
        
        
    }
}
