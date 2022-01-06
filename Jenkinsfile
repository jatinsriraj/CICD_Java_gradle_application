pipeline{
    agent any{
        label "node"
    }
    stages{
        stage("sonar quality check"){
            agent {
                docker {
                    image 'openjdk:11'
                }
            }            
            steps{
                script{
                    withSonarQubeEnv(credentialsId: 'sonar-token') {
                        sh 'chmod+X gradlew'
                        sh './gradlew sonarqube'
                    }
                }
            }
        }
    }
}    