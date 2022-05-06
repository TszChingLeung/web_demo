pipeline{
    agent any
    
    stages{
        stage('pull code'){
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: '4198fce9-b0a4-4c32-a295-332fd351ef4e', url: 'git@github.com:TszChingLeung/web_demo.git']]])
            }
        }
        stage('build project'){
            steps{
                bat 'mvn clean package'
            }
        }
        stage('publish project'){
            steps{
                deploy adapters: [tomcat8(credentialsId: '4198fce9-b0a4-4c32-a295-332fd351ef4e', path: '', url: 'http://192.168.3.34:8081/')], contextPath: null, war: 'target/*.war'
            }
        }
    }
}
