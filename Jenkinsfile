pipeline{
    agent any
    tools{
        maven 'maven'
    }
    stages{
        stage("Build"){
            steps{
                sh 'mvn clean package'
            }
//             post{
//                 success{
//                     echo "Archiving the artifacts"
//                     archiveArtifacts artifacts: '**/target/*.war'
//                 }
//             }
        }
        // stage("clone"){
        //     steps{
        //         git 'https://github.com/DungLL183/jenkins-github.git'
        //     }
        // }
        stage("Deploy to tomcat server"){
            steps{
                deploy adapters: [tomcat9(credentialsId: '5eca4d1e-307b-496a-b867-2a5a9b9f1e67', path: '', url: 'http://43.201.19.50:8088')], contextPath: null, war: '**/*.war'            }
        }
    }
}
