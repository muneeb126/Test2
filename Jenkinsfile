pipeline {
      options{    // This is used for log rotation

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
    stage("Build"){

   steps{

   // Running basic maven command , you can pass argument to this command also like DskipTests exec:java -Dexec.args="some value"

     sh 'mvn --version' 
        'mvn sonar:sonar'
   }
   }
stage("Sonar analysis"){

   steps{

 script{

 // These are some args used to run sonar analysis, as per your application configure these value

   def args = [

                "-Dsonar.host.url=sonar_url",

                "-Dsonar.projectBaseDir=.",

                "-Dsonar.sources=src/main",

                "-Dsonar.tests=src/test",

                "-Dsonar.sourceEncoding=UTF-8",

                "-Dsonar.binaries=target/classes",

                "-Dsonar.java.coveragePlugin=jacoco",

                "-Dsonar.language=java",

                "-Dsonar.dynamicAnalysis=reuseReports",

                "-Dsonar.junit.reportPaths=target/surefire-reports,target/failsafe-reports",

                "-Dsonar.jacoco.reportPaths=target/jacoco.exec,target/jacoco-it.exec"

        ]

  

  sh "org.sonarsource.scanner.maven:sonar-maven-plugin:3.3.0.603:sonar $args"

 }

   }

  }

  }
    
}
