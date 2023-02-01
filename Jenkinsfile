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
                sh "mv target/*.jar target/myapp.jar"
                
             }
        }
        stage("deploy to tomcat"){
            steps{
               sshagent(['tomcat-new']) {
                sh """
                   scp -o StrictHostKeyChecking=no target/myapp.jar ec2-user@172.31.53.86:/opt/tomcat8/webapps/
                   ssh ec2-user@172.31.53.86 /opt/tomcat8/bin/shutdown.sh
                   ssh ec2-user@172.31.53.86 /opt/tomcat8/bin/startup.sh
                   
                   """
}
              
            }
        }
    }
}
