node('built-in')
{
   stage('ContionousDownload')
   {
    git 'https://github.com/intelliqittrainings/maven.git'
   }
   
   stage('ContionousBuild')
   {
    sh 'mvn package'
   }
   
   stage('ContionousDownload')
   {
    deploy adapters: [tomcat9(credentialsId: 'tomcat-server', path: '', url: 'http://172.31.31.174:8080')], contextPath: 'teatapp', war: '**/*.war'
   }
   
   stage('ContionousTesting')
   {
    git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
    sh 'java -jar /root/.jenkins/workspace/ScriptedPipeline/testing.jar'
   }
   
   stage('ContionousDelivery')
   {
    input id: 'Srinivas', message: 'Get approval from Delivery Manager'   
    deploy adapters: [tomcat9(credentialsId: 'tomcat-server', path: '', url: 'http://172.31.23.99:8080')], contextPath: 'prodapp', war: '**/*.war'
   }
}
