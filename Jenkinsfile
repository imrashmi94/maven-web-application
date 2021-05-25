node
{
    
    def mavenHome = tool name: "maven3.8.1"
    
    properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), pipelineTriggers([pollSCM('* * * * *')])])
    
    stage('Checkout Code')
    {
        git branch: 'development', credentialsId: '5c1f38c7-bf61-4308-927b-0343b97b8001', url: 'https://github.com/imrashmi94/maven-web-application.git'
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
      sshagent(['b796d8a7-3cd3-47cb-9432-fffff99689a5']) {
      sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@3.104.74.194:/opt/apache-tomcat-9.0.45/webapps/"
    }
    }
    */
    stage('SendEmailNotification')
    {
       emailext body: '''Build over...
Regards,
Mithun Technologies,
6360620646''', subject: 'Build over...', to: 'imrashmik94@gmail.com'
    }
    
}
