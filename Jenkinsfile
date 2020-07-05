pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh label: 'Build', script: './gradlew build'
            }
        }
        stage("Archive") {
            steps {
                archiveArtifacts artifacts: 'app/build/outputs/apk/release/*.apk,app/build/outputs/apk/release/*.json', followSymlinks: false
            }
        }
    }
}
