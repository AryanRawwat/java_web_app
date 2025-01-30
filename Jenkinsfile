pipeline {
    agent any

        tools {
        maven 'maven-3'  
       }

    stages {
         stage('git clone') {
            steps {
              git branch: 'main', credentialsId: 'jenkins-github', url: 'https://github.com/AryanRawwat/java_web_app.git'
            }
        }

          stage('build') {
            steps {
               sh 'mvn clean package'
            }
        }
          stage('SonarQube analysis') {
            steps {
               withSonarQubeEnv('Sonar-9'){
                  sh 'mvn sonar:sonar'
               }
            }
          }

         stage('upload artifact') {
            steps {
               nexusArtifactUploader artifacts: [[artifactId: 'my-web-app', classifier: '', file: 'target/my-web-app-1.0-SNAPSHOT.war', type: 'war']], credentialsId: 'nexus-credentials', groupId: 'com.example', nexusUrl: '52.66.203.158:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'java-web-app-repo', version: '1.0-SNAPSHOT'
            }
        }
    }
}
