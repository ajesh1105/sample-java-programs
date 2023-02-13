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
                
            nexusArtifactUploader artifacts: [[artifactId: 'java-samples', classifier: '',
             file: 'memoryref/target/memoryref.jar', type: 'jar']], credentialsId: 'nexus3', 
            groupId: 'com.github.chrishantha.sample', nexusUrl: '172.31.20.36:8081', nexusVersion: 'nexus3', 
             protocol: 'http', repository: 'simple-java-snapshot/', version: '0.0.2-SNAPSHOT'
                }
              
            }
        stage("deploy to tomcat"){
            steps{
                sshagent(['tomcat-new']) {

   sh 'scp -o StrictHostKeyChecking=no ubuntu@100.25.12.30 memoryref/target/memoryref.jar ec2-user@172.31.53.86:/opt/tomcat8/webapps/'
}
                
                  }
        }
        
        
    }

}
