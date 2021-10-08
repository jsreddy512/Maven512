node('master') 
{
  stage('ContinousDownload') 
  {
    git 'https://github.com/intelliqittrainings/maven.git'
}
 stage('ContinousBuild') 
  {
   sh 'mvn package'
  }
   stage('ContinousDeployment')
  {
   deploy adapters: [tomcat9(credentialsId: '57694aab-c894-4d3f-9306-22ada2979d1c', path: '', url: 'http://172.31.35.23:8080')], contextPath: 'testapp', war: '**/*.war'
}
stage('ContinousTesting') 
  {
   git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
   sh 'java -jar /var/lib/jenkins/workspace/ScriptedPipeline/testing.jar'
  }
  stage('ContinousDelivery') 
  {
   deploy adapters: [tomcat9(credentialsId: '57694aab-c894-4d3f-9306-22ada2979d1c', path: '', url: 'http://172.31.47.30:8080')], contextPath: 'prodapp', war: '**/*.war'
}
}
