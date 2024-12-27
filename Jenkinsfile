pipeline {
    agent any

    stages {
        stage('Test') {

            // Lancement des tests unitaires.
            steps {
                bat "./gradlew test"
            }

            // Archivage des résultats des tests unitaires.
            post {
                always {
                    junit 'build/test-results/**/*.xml'
                }
            }

            //Génération des rapports de tests Cucumber
            steps {
                bat "./gradlew cucumber"
            }
        }
    }

}