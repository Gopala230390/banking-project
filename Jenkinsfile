pipeline {
  agent any 
  tools {
     maven 'M2_HOME'
        }
stages {
     stage('Git Checkout') {
       steps {
         git 'https://github.com/devopscbabu/Project-Banking-May23.git'
             }
        }
     stage('Build Package') {
       steps {
         sh 'mvn package'
       }
     }
     stage('Publish HTML Reports') {
       steps {
         publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: '/var/lib/jenkins/workspace/BankingProject/target/surefire-reports', reportFiles: 'index.html', reportName: 'HTML Report', reportTitles: '', useWrapperFileDirectly: true])
             }
         }
     stage('Create Docker image of App') {
       steps {
         sh 'docker build -t cbabu85/Banking-app:1.0 .'
             }
         }
    }
}
