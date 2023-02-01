pipeline{
    agent any
    
    
    stages{
        stage("Git Checkout"){
            steps{
                https://github.com/ajesh1105/sample-java-programs
            }
        }
        stage("Maven Build"){
            steps{
                sh "mvn clean package"
                sh "mv target/*.war target/myweb.war"
            }
        }}}
