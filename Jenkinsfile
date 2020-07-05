pipeline {
    agent any

    stages {
        stage("ChangeLog") {
            steps {
                sh label: 'Get Change Log', script: 'curl -s "http://192.168.161.244:8080/job/kalo/107/api/xml?wrapper=changes&xpath=//changeSet//comment" --user "sunwei:11eb26283ad0de235fb6442b9a8bc50514"'
            }
        }
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