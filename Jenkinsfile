node('built-in')
{
    stage('ContinuousDownload') 
    {
         git 'https://github.com/intelliqittrainings/maven.git'
    }
    stage('ContinuousBuild') 
    {
         sh 'mvn package'
    }
    stage('ContinuousDeployment')
    {
        deploy adapters: [tomcat9(credentialsId: 'ef64fce5-f11a-43dc-9520-ba6a5eb57d31', path: '', url: 'http://172.31.20.40:8080')], contextPath: 'testapp', war: '**/*.war'
    }
    stage('ContinuousTesting')
    {
        git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
        sh 'java -jar /home/ubuntu/.jenkins/workspace/ScriptedPipeline/testing.jar'
        
    }
    stage('ContinuousDelivery')
    {
        
        deploy adapters: [tomcat9(credentialsId: 'ef64fce5-f11a-43dc-9520-ba6a5eb57d31', path: '', url: 'http://172.31.25.20:8080')], contextPath: 'prodapp', war: '**/*.war'
    }
    
    
    
    
   }
