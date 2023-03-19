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
                sh """export PATH=/usr/lib/jvm/java-8-openjdk-amd64/bin:$PATH
                      mvn package"""
            }    
        }
        stage('archive'){
            steps{
                archiveArtifacts artifacts: '**/target/*.war', 
                followSymlinks: false
            }
        }
        stage('JUNIT'){
            steps{
                junit '**/surefire-reports.xml'
            }
        }

    }
}
