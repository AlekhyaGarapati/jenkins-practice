pipeline{
agent {node { label 'agent1'} }
environment{
    user = 'alekhya'
}
    
stages {
    stage ('example') {
        environment{
            auth = credentials('ssh-auth')
        }
        steps{
            echo "printenv - prints all environemnt variables. We can use them in program if needed"
            sh 'printenv' 
            sh 'echo "user name : $USER"'
        }
    }
    stage ('build'){
        steps{
            echo "build from webhook test"
            sh '''
             ls -ltr
             pwd
            '''
        }
    }
    stage ('scan') {
        steps{
            echo "scan"
        }
    }
    stage ("deploy"){
        steps{
            echo "deploy"
        }
    }
}
post {
    always{
        echo "i will execute always after job completion"
    }
    success {
        echo "i will execute only after job completion is success"
    }
    failure {
        echo "i will execute only after job completion is failure"
    }
}
}