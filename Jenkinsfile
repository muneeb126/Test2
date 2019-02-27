pipeline {
    options {    // This is used for log rotation

        buildDiscarder(logRotator(numToKeepStr: '5'))

        disableConcurrentBuilds()

    }

    agent {
        label "windows"
    }
    tools {
        maven 'M3'
        jdk 'JDK 1.8'
    }
    stages {
        stage("Build") {

            steps {

                // Running basic maven command , you can pass argument to this command also like DskipTests exec:java -Dexec.args="some value"

                sh 'mvn --version'
            }
            post {

                success {

                    // this is used to send a mail when job is successful

                    script {

                        def content = "Email message that should be in body part of email"

                        emailext attachLog: true, body: content, contentType: 'text/html', subject: success, from: 'acb@email.com', to: "muhammad.zafar@mastercard.com"

                    }

                }
            }
        }
    }
}
