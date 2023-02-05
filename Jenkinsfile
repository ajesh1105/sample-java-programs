pipeline{
    agent any
    stages{
        stage("Git Checkout"){
            steps{
               git 'https://github.com/ajesh1105/sample-java-programs'
            }
        }
        stage("Maven Build"){
            steps{
                sh "mvn clean package"
                
                  }
        }
        stage("upload to nexus"){
            steps{
                def mavenPOM = readMavenPom 'pom.xml'
             nexusArtifactUploader artifacts: [[artifactId: 'java-samples', classifier: '', file: 'memoryref/target/memoryref.jar', type: 'jar']], credentialsId: 'nexus3', groupId: 'com.github.chrishantha.sample', nexusUrl: '172.31.20.36:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'simple-java-snapshot/', version: "${mavenPom.version}"
              
            }
        }
    }

}
