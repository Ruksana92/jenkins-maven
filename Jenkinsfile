pipeline {

    agent any

    tools {

        maven "maven395"
    }

    
    stages {
        stage('Build Maven') {
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'GIT_REPO', url: 'https://github.com/Ruksana92/jenkins-maven.git']]])

                sh "mvn -Dmaven.test.failure.ignore=clean test package"
                
            }
            stage {'Archive Artifacts'}{
                  archiveArtifacts artifacts: 'target/*.jar'
            }    
        }
    }
    
}
