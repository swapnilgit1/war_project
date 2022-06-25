pipeline{
    agent any
    tools {
        maven 'Maven' 
    }


    stages{

        stage("Unite_Test"){
            steps{                                                 //mvn test
                sh 'mvn test'
            }

        }


        stage("Build"){                                           //mvn install
            steps{
                sh 'mvn package'
            }

        }


        stage("Deploy_to_Test"){                                //deploy to container plugin
            steps{
               deploy adapters: [tomcat9(credentialsId: 'tomcat_server_details_1', path: '', url: 'http://13.126.65.202:8585')], contextPath: '/app', war: '**/*.war'
            }

        }

        
        stage("Deploy_to_Prod"){                                   //deploy to container plugin
            steps{
                deploy adapters: [tomcat9(credentialsId: 'tomcat_server_details_1', path: '', url: 'http://13.235.104.82:9595')], contextPath: '/app', war: '**/*.war'
            }

        }






    }



    post{
        
        success{
            echo "EVERYTHINF IS SUCESSFULL"
        }
        failure{
            echo "THERE ARE ISSUES WITH PIPELINE"
        }
    }
}
