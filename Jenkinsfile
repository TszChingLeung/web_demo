pipeline {
   agent any

   stages {
      stage('pull code') {
         steps {
            checkout([$class: 'GitSCM', branches: [[name: '*/${branch}']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'b632ed00-fc81-43c8-a746-5aa0673b2658', url: 'git@192.168.66.100:itheima_group/web_demo.git']]])
         }
      }
      stage('build project') {
         steps {
            sh 'mvn clean package'
         }
      }
      stage('publish project') {
         steps {
            deploy adapters: [tomcat8(credentialsId: 'fc23e5b7-9930-4dfb-af66-a2a576be52fb', path: '', url: 'http://192.168.66.102:8080')], contextPath: null, war: 'target/*.war'
         }
      }

   }
   post{

   }
}