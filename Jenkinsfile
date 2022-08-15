node('built-in') 
{
    stage('ContinuousDownload') 
    {
          git 'https://github.com/krishnain/newmaven1.git'
    }
    stage('ContinuousBuild') 
    {
          sh 'mvn package'
    }
    
    stage('ContinuousDeployment') 
    {
          sh label: 'Jenkinsfile', script: 'scp /root/.jenkins/workspace/scripted/webapp/target/webapp.war ubuntu@172.31.31.174:/var/lib/tomcat9/webapps/tapp.war'
    }
    
    stage('ContinuousTesting') 
    {
          git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
          sh 'java -jar /root/.jenkins/workspace/scripted/testing.jar'
          
          
    }
    
    stage('ContinuousDelivery') 
    {
          input id: 'Srinivas', message: 'Take approval from delivery Manager'
          sh label: 'Jenkinsfile', script: 'scp /root/.jenkins/workspace/scripted/webapp/target/webapp.war ubuntu@172.31.23.99:/var/lib/tomcat9/webapps/papp.war'
    }
}
