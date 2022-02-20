pipeline
{
    agent any
    stages
    {
        stage('continuous_download_loans')
        {
          steps
          {
             git 'https://github.com/supriyalad/maven.git' 
          }
        }
        stage('continuous_build_loans')
        {
          steps
          {
              sh 'mvn package' 
          }
        }
    }
}
