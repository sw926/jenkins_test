pipeline {
    agent any

    stages {
        stage("ChangeLog") {
            steps {
                sh label: 'Get Change Log', script: ' curl -s "http://127.0.0.1:8080/job/kalo-dev/11/api/xml?wrapper=changes&xpath=//changeSet//comment" --user "sunwei:11eb26283ad0de235fb6442b9a8bc50514" | sed -e "s/<\\/comment>//g; s/<comment>/* /g; s/<\\/*changes>//g" | sed \'/^$/d;G\' | sed \'/^$/d\''
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