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
                deploy adapters: [tomcat9(credentialsId: '4147316f-870b-4aea-803e-6e088569c7d1', path: '', url: 'http://3.37.130.119:8088')], contextPath: null, war: '**/*.war'
                        }
        }
    }
}
