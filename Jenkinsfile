pipeline{
    agent{
        label 'hi'
    }
    triggers{
        pollSCM('* * * * *')
    }
    stages{
        stage('clone'){
            steps{
                git url: 'https://github.com/lahari104/game-of-life.git',
                    branch : 'moon'
            }
        }
        stage('package'){
            steps{
                sh """mvn package"""
            }
        }
    }
}
