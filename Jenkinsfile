pipeline {
    agent any

    stages {
         stage('git clone') {
            steps {
              git branch: 'main', credentialsId: 'jenkins-github', url: 'https://github.com/AryanRawwat/java_web_app.git'
            }
        }
        
    }
}
