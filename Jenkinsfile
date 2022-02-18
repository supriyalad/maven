pipeline
{
    agent any
    stages
    {
        stage('continuous_download')
        {
          steps
          {
             git 'https://github.com/supriyalad/maven.git' 
          }
        }
        stage('continuous_build')
        {
          steps
          {
              sh 'mvn package' 
          }
        }
        stage('continuous_deploy')
        {
            steps
            {
                sh 'scp /home/ubuntu/.jenkins/workspace/declarative_pipeline/webapp/target/webapp.war ubuntu@172.31.91.148:/var/lib/tomcat9/webapps/test2app.war'
            }
        }
        stage('continuous_testing')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                sh 'java -jar /home/ubuntu/.jenkins/workspace/declarative_pipeline/testing.jar'
            }
        }
        stage('continuous_delivery')
        {
            steps
            {
                input message: 'Need approval from DM', submitter: 'manager'
                sh 'scp /home/ubuntu/.jenkins/workspace/declarative_pipeline/webapp/target/webapp.war ubuntu@172.31.87.233:/var/lib/tomcat9/webapps/prod2app.war'
            }
        }
    }
}
