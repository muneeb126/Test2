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
// Always runs. And it runs before any of the other post conditions.
        success {
            mail(from: "bob@example.com",
                    to: "steve@example.com",
                    subject: "That build passed.",
                    body: "Nothing to see here")
        }
        failure {
            mail(from: "bob@example.com",
                    to: "steve@example.com",
                    subject: "That build failed!",
                    body: "Nothing to see here")
        }
    }
        }
    }
}
