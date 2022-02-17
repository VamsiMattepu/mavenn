pipeline
{
 agent any
 stages
 {
  stage('ContinosDownload') 
  {
   steps
   {
     git 'https://github.com/intelliqittrainings/maven.git' 
   }
  }
  stage('ContinosBuild') 
  {
   steps
   {
    sh 'mvn package'
   }
  }
  stage('ContinosDeploy') 
  {
   steps
   {
    deploy adapters: [tomcat9(credentialsId: '457d8081-2137-478a-8c21-dc1fa233816e', path: '', url: 'http://172.31.36.186:8080')], contextPath: 'qnapp', war: '**\\*.war'
   }
  }
  stage('ContinosTesting') 
  {
   steps
   {
    git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
    sh 'java -jar /home/ubuntu/.jenkins/workspace/DeclarativePipeline/testing.jar'
   }
  }
  stage('ContinosDelivery') 
  {
   steps
   {
    deploy adapters: [tomcat9(credentialsId: '457d8081-2137-478a-8c21-dc1fa233816e', path: '', url: 'http://172.31.38.171:8080')], contextPath: 'pnapp', war: '**\\*.war'
   }
  }
 }
}
