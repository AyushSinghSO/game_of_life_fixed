pipeline{
    tools{
        jdk 'myjava'
        maven 'mymaven'
    }
    agent none
      stages{
          stage('Checkout'){
              agent any
              steps{
                  git branch:'main',url:'https://github.com/devops-trainer/game-of-life.git'
              }
          }
          stage('Compile'){
              agent any
              steps{
                  bat 'mvn compile'
              }
          }
          stage('UnitTest'){
              agent{label 'win_slave'}
              steps{
                  git branch:'main',url:'https://github.com/devops-trainer/game-of-life.git'
                  bat 'mvn test'
              }
              post{
                  always{
                      junit 'gameoflife-web/target/surefire-reports/*.xml'
                  }
              }
          }
          stage('Package'){
              agent any
              steps{
                  bat 'mvn package'
              }
          }
         
      }
    
}
