

pipeline {
    /* a Declarative Pipeline */
    agent any

    stages {
        stage('Build'){
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Now archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage('Deploy to Staging'){
            step {
                build job: 'deploy-to-staging'
            }
        }
    }
}