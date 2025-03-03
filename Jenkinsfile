pipeline {
    agent any

    triggers {
        cron('H/3 * * * 1') // Trigger every 3 minutes on Mondays
    }

    stages {
        stage('Build') {
            steps {
                script {
                    // Commands for building the project
                    sh './mvnw clean install'
                }
            }
        }

        stage('Code Coverage') {
            steps {
                script {
                    // Commands to run JaCoCo and generate coverage report
                    sh './mvnw jacoco:report'
                }
            }
        }

        stage('Publish Report') {
            steps {
                script {
                    // Publish JaCoCo report
                    junit '**/target/test-classes/*.xml'
                    jacoco()
                }
            }
        }
    }
}
