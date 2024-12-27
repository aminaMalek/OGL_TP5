pipeline {
   options {
        timeout(time: 1, unit: 'MINUTES')
    }

    agent any

    stages {
        stage('Test') {
            steps {
                // Lancement des tests unitaires.
                bat "./gradlew test"
            }
            post {
                // Archivage des résultats des tests unitaires.
                always {
                    junit 'build/test-results/**/*.xml'
                }
            }
        }

        stage('SonarQube analysis') {
            steps {
                withSonarQubeEnv('sonar') {
                // Lancement de l'analyse statique du code.
                   bat "./gradlew sonar"
                }


            }
        }

        stage('Code Quality') {
             steps {
                    waitForQualityGate abortPipeline: true
             }
        }
    }
}
