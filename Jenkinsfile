pipeline{
    agent any
    tools {
        maven '3.8.6' 
    }
    stages{
        stage("Test"){
            steps{
                // mvn test
                sh "mvn test"
             }
          }
          stage("Build"){
            steps{
                sh "mvn package"
             }
          }
          stage("Deploy to Test"){
            steps{
                // deploy on container -> plugin
                deploy adapters: [tomcat9(credentialsId: 'Tomcat', path: '', url: 'http://192.168.146.141:8080/')], contextPath: 'ROOT', onFailure: false, war: '**/ROOT.war'
             }
          }
          stage("File Trasfer"){
            steps{
                echo "========executing A========"
             }
          }
          stage("Deploy to Prod"){
            steps{
                echo "========executing A========"
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
