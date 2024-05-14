pipeline{
    agent {
        label 'tomcat'
    }
    triggers{
        pollSCM('* * * * *')
    }
    stages{
        stage('clone'){
            steps{
                git url: "https://github.com/lahari104/game-of-life.git",
                    branch: 'tomcat'
            }
        }
        stage('build'){
            steps{
                sh 'sudo apt install maven -y'
                sh 'mvn clean package'
                sh 'sudo apt update'
                sh 'sudo apt install tomcat9 -y'
                sh 'sudo cp -r /home/ubuntu/tomcat/workspace/tomcat/gameoflife-web/target/gameoflife.war   /var/lib/tomcat9/webapps'
                sh 'sudo systemctl daemon -reload'
                sh 'sudo systemctl restart tomcat9.service'
            }
        }
    }
}