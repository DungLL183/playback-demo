pipeline{
    agent any
    tools{
        maven 'local_maven'
    }
    stages{
        stage("Build"){
            sh 'mvn clean package'
        }
        post{
            sucess{
                echo "Archiving the Artifacts"
                archiveArtifacts artifacts: '**/target/*.war'
            }
        }
        stage("Deploy to tomcat server"){
            steps{
                deploy adapters: [tomcat9(credentialsId: '4147316f-870b-4aea-803e-6e088569c7d1', path: '', url: 'http://43.201.109.191:8088')], contextPath: null, war: '**/*.war'
            }
        }
    }
}