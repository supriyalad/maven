pipeline
{
    agent any
    stages
    {
        stage('continuous_download_master')
        {
          steps
          {
             git 'https://github.com/supriyalad/maven.git' 
          }
        }
        stage('continuous_build_master')
        {
          steps
          {
              sh 'mvn package' 
          }
        }
        stage('continuous_deploy_master')
        {
            steps
            {
                sh 'scp /home/ubuntu/.jenkins/workspace/declarative_pipeline/webapp/target/webapp.war ubuntu@172.31.91.148:/var/lib/tomcat9/webapps/test2app.war'
            }
        }
        stage('continuous_testing_master')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                sh 'java -jar /home/ubuntu/.jenkins/workspace/declarative_pipeline/testing.jar'
            }
        }
        stage('continuous_delivery_master')
        {
            steps
            {
                # input message: 'Need approval from DM', submitter: 'manager'
                sh 'scp /home/ubuntu/.jenkins/workspace/declarative_pipeline/webapp/target/webapp.war ubuntu@172.31.87.233:/var/lib/tomcat9/webapps/prod2app.war'
            }
        }
    }
}
