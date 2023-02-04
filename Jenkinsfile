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
              nexusArtifactUploader artifacts: [[artifactId: 'java-samples', classifier: '', file: 'target/memoryref.jar', type: 'jar']], credentialsId: 'nexus3', groupId: 'com.github.chrishantha.sample', nexusUrl: '172.31.20.36', nexusVersion: 'nexus3', protocol: 'http', repository: 'http://3.85.212.119:8081/repository/simple-java-snapshot/', version: '0.0.2-SNAPSHOT'
                  }
              
            }
        }
    }

