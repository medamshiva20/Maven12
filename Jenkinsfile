pipeline
{
    agent any
    stages
    {
        stage('ContinuousDownload')
        {
            steps
            {
                script
                {
                    try
                    {
                     git 'https://github.com/medamshiva20/JavaProject.git'   
                    }
                    catch(Exception e1)
                    {
                        mail bcc: '', body: 'Download the code from git hub', cc: '', from: '', replyTo: '', subject: 'Download the code', to: 'gitadmin@outlook.com'
                        exit(1)
                    }
                }
            }
        }
        stage('ContinuousBuild')
        {
            steps
            {
                script
                {
                    try
                    {
                        sh label: '', script: 'mvn package'
                    }
                    catch(Exception e2)
                    {
                       mail bcc: '', body: 'Build the code ', cc: '', from: '', replyTo: '', subject: 'Build the code', to: 'build@outlook.com'
                       exit(1)
                    }
                }
            }
        }
        stage('ContinuousDeployment')
        {
            steps
            {
                script
                {
                    try
                    {
                        sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/Decpipeline2/webapp/target/webapp.war ubuntu@172.31.60.100:/var/lib/tomcat8/webapps/dtapp22.war'
                    }
                    catch(Exception e3)
                    {
                        mail bcc: '', body: 'Deploy the code', cc: '', from: '', replyTo: '', subject: 'Deploy the code', to: 'deploy@outlook.com'
                        exit(1)
                    }
                }
            }
        }
        stage('ContinuousTesting')
        {
            steps
            {
                script
                {
                    try
                    {
                        git 'https://github.com/medamshiva20/FunctionalTesting.git'
                        sh label: '', script: 'java -jar /home/ubuntu/.jenkins/workspace/Decpipeline2/testing.jar'
                    }
                    catch(Exception e4)
                    {
                        mail bcc: '', body: 'Testing the application', cc: '', from: '', replyTo: '', subject: 'Testing the application', to: 'testing@outlook.com'
                        exit(1)
                    }
                }
            }
        }
        stage('ContinuousDelivery')
        {
            steps
            {
                script
                {
                    try
                    {
                        sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/Decpipeline2/webapp/target/webapp.war ubuntu@172.31.62.253:/var/lib/tomcat8/webapps/dpapp22.war'
                    }
                    catch(Exception e5)
                    {
                        mail bcc: '', body: 'Deliver the application', cc: '', from: '', replyTo: '', subject: 'Deliver the application', to: 'delivery@outlook.com'
                        exit(1)
                    }
                }
            }
        }
    }
}
