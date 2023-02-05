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
                
            nexusArtifactUploader artifacts: [[artifactId: 'java-samples', classifier: '', file: 'memoryleak/target/memoryleak-0.0.2-SNAPSHOT-shaded.jar', 
                                               type: 'jar']], credentialsId: 'nexus3', groupId: 'com.github.chrishantha.sample', nexusUrl: '172.31.20.36:8081',
                                                nexusVersion: 'nexus3', protocol: 'http', 
                                               repository: 'http://34.228.70.134:8081/repository/demo-snapshot-0.0.2', version: '0.0.2'
                }
              
            }
        
    }

}
