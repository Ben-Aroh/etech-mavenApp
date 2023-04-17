pipeline {
  agent any
  tools {
    maven 'maven'
  }
  stages{
    stage('1-git-clone'){
      steps{
        checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'github-id', url: 'https://github.com/Ben-Aroh/etech-mavenApp.git']]])
      }
    }
    stage('2-cleanws'){
      steps{
        sh 'mvn clean'
      }
    }
    stage('3-mavenbuild'){
      steps{
        sh 'mvn package'
      }
    }
    stage('unittest'){
        steps{
            sh 'mvn test'
        }
    }
    stage('codequality'){
        steps{
       sh 'mvn clean verify sonar:sonar -Dsonar.projectKey=team5codereview -Dsonar.projectName="team5codereview" -Dsonar.host.url=http://ec2-54-80-186-13.compute-1.amazonaws.com:9000 -Dsonar.token=sqp_e1aa77ad7ebfec56e06f944bc84e4e2688118b08'
        }
    }
  }
}
 
