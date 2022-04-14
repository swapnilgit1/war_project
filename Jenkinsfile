pipeline
{
    agent any

    tools
    {
        maven 'maven'
    }


    stages
    {
        stage("Test")
        {
            steps
            {
                //mvn test
                sh 'mvn test'
               
            }
            
        }



     stage("Build")
     {
            steps
            { 
                //mvn install
                sh 'mvn clean install'
               
            }     
     }



         stage("Deploy on Test")
         {
            steps
            {
                //container plugin
                deploy adapters: [tomcat9(credentialsId: '329cb5dc-c2c7-47bc-a535-b7c77cda309e', path: '', url: 'http://3.110.115.196:8085')], contextPath: '/app', war: '**/*.war'
               
            }
            
        }


            
    


    }
    







    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }


}
