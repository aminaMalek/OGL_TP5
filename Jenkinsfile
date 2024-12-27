pipeline {
    agent any

    stages {
        stage('Test') {
            steps {
                // Lancement des tests unitaires.
                bat "./gradlew test"

                // Génération des rapports de tests Cucumber.
                bat "./gradlew cucumber"
            }
            post {
                // Archivage des résultats des tests unitaires.
                always {
                    junit 'build/test-results/**/*.xml'
                }
            }
        }
    }
}
