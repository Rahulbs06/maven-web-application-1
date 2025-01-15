node
{
    properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '5', artifactNumToKeepStr: '5', daysToKeepStr: '5', numToKeepStr: '5')), pipelineTriggers([pollSCM('* * * * *')])])
    def mavenHome = tool name: "Maven 3.9.9"
    stage('get the code')
    {
        git branch: 'development', credentialsId: 'ec62e8f0-5466-4bc0-86c5-5bdee33130d2', url: 'https://github.com/Rahulbs06/maven-web-application-1.git'
    }
    stage('build')
    {
        sh "${mavenHome}/bin/mvn clean package"
    }
    stage('test')
    {
        sh "${mavenHome}/bin/mvn sonar:sonar deploy"
    }
    stage('DeployApp')
    {
    sshagent(['9f867e92-5957-47bd-bfc9-9c53c3b6573e']) 
    { 
        sh "scp -o  StrictHostKeyChecking=no target/maven-web-application.war ubuntu@3.89.183.211:/opt/apache-tomcat-9.0.65/webapps/"
    }
    

}
}
