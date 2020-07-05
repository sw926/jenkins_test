pipeline {
    agent any


    stages {
        stage('Build') {
            steps {
                sh label: 'Build', script: './gradlew build'
            }
        }

        stage("ZipApk") {
            steps {
                sh label: 'zip apk', script: 'zip -q -o -r -j kalo.zip app/build/outputs/apk/release/*'
            }
        }
    }
}