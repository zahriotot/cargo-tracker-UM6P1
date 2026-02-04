pipeline {
    agent any

    triggers {
        githubPush()   
    }

    stages {

        stage('Clone') {
            steps {
                git branch: 'develop', url: 'https://github.com/karima889/cargo-tracker-UM6P1'
            }
        }

        stage('Build & Test') {
            steps {
                bat 'mvnw.cmd clean package'
            }
        }
    }

    post {
        success {
            echo 'Build réussi !'
            archiveArtifacts artifacts: 'target/*.war', fingerprint: true
        }
        failure {
            echo 'Build échoué'
        }
    }
}
