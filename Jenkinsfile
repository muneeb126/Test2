pipeline {
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

     sh 'mvn clean' 
   }
   }

  }
    
}
