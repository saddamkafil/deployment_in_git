pipeline
{
    agent{
    label 'ProdServer'}
    triggers 
    {
    pollSCM '* * * * *'
    }
    stages
    {
        stage('Download')
        {
            steps
            {
                git 'https://github.com/saddamkafil/deployment_in_git.git'
            }
        }
        stage('build')
        {
        steps{
                script {
                  def mvnhome = tool name: 'M2_HOME', type: 'maven'
                  sh "${mvnhome}/bin/mvn --version"
                  sh "${mvnhome}/bin/mvn clean package"
                }
                }
        }
                stage('move war file to docker container')
                {
                    steps{
                     sh'pwd'
                     sh'mv /home/ec2-user/workspace/prod1/webapp/target/webapp.war /home/ec2-user/workspace/prod1/'
                     sh'ls -l'
                     }
                }
                }
                }
