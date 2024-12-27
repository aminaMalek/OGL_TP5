pipeline {
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
    }
}
