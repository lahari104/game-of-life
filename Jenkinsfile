pipeline{
    agent {
        label 'tomcat'
    }
    stages{
        stage('clone'){
            steps{
                git url"https://github.com/lahari104/game-of-life.git"
                branch 'tomcat'
            }
        }
        stage('build'){
            steps{
                sh 'sudo apt install maven -y'
                sh 'mvn clean package'
                sh 'sudo apt install tomcat9 -y'
            }
        }
    }
}