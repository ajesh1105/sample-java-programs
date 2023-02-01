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
        stage("deploy to tomcat"){
            steps{
                sshagent(['tomcat8']) {
                sh """
                   scp -o StrictHostKeyChecking=no target/memoryref.jar ec2-user@172.31.53.86:/opt/tomcat8/webapps/
                   ssh ec2-user@172.31.53.86 /opt/tomcat8/bin/shutdown.sh
                   ssh ec2-user@172.31.53.86 /opt/tomcat8/bin/startup.sh
}
              
            }
        }
    }
}
