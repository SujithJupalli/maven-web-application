node 
{
    def mavenHome = tool name: "maven3.8.1"
    
    properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), pipelineTriggers([pollSCM('* * * * *')])])
    
    stage('CheckoutCode')
    {
   git branch: 'development', credentialsId: '177451e3-1929-4cfe-a11f-51b567d5de06', url: 'https://github.com/SujithJupalli/maven-web-application.git'
    }

    stage('Build')
{
    sh "${mavenHome}/bin/mvn clean package"
    
}
/*
stage('ExecuteSonarQubeReport')
{
    sh "${mavenHome}/bin/mvn sonar:sonar"
}
 stage('UploadArtifactsintoNexus')
{
    sh "${mavenHome}/bin/mvn deploy"
}
stage('DeployAppintoTomcatServer')
{
sshagent(['63d85a8a-352a-450b-9e7d-13000cd5f1c2']) {
sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@65.0.99.142:/opt/apache-tomcat-9.0.45/webapps/"
}
}
*/
stage('SendEmailNotification')
{
emailext body: '''Build Over ..

Regards 
jack pirate''', subject: 'Build Over ...', to: 'jupallisujith@gmail.com'
}
}
