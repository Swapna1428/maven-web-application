node{
    
    echo "The job name is: ${env.JOB_NAME}" 
    echo "The build number is ${env.BUILD_NUMBER}" 
    echo "The node name is ${env.NODE_NAME}" 
    properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), pipelineTriggers([pollSCM('* * * * *')])])
    
    def  mvnHome = tool name: 'maven 3.9.1'
    stage('checkoutCode'){
        git branch: 'development', credentialsId: 'b7369d52-23ad-42d4-a4eb-b5e2de6cb172', url: 'https://github.com/Swapna1428/maven-web-application.git'
    }
    stage('Build'){
        sh "${mvnHome}/bin/mvn clean package"
    }
  /*
    stage('executeSonarqubeReport'){
        sh "${mvnHome}/bin/mvn clean sonar:sonar"
    }
    stage('uploadArtifactsIntoNexus'){
        sh "${mvnHome}/bin/mvn clean deploy"
    }
    stage('DeployAppIntoTomcatServer'){
        sshagent(['11772e09-5430-4aee-9173-a48a60481e11']) {
    sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@172.31.47.153:/opt/apache-tomcat-9.0.73/webapps/"
}
    }
    */
}
