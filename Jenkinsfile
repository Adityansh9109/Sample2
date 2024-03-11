pipeline{
    agent any 
    tools {
        maven 'Maven'
    }
     environment {
        JAVA_HOME = 'C:\Program Files\Java\jdk-17'  // Set the correct path to your JDK
    }
    stages{
        stage('Build'){
            steps{
                bat 'mvn clean package'
            }
            post{
                success{
                    echo "archiving the artifacts"
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage('Deploy to tmact server'){
            steps{
                deploy adapters: [tomcat8(credentialsId: 'a8b453a0-25a0-493b-b976-f10d997066af', path: '', url: 'http://localhost:9090/')], contextPath: null, war: '**/*.war'
            }
            
        }
    }
}
