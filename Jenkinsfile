pipeline{
agent {node { label 'agent1'} }
environment{
    user = 'alekhya'
}
stages {
    stage ('environment') {
        steps{
            echo "printenv - prints all environemnt variables. We can use them in program if needed"
            sh 'printenv' 
            echo "printenv.user - prints user name declared above from env variables"
            sh 'printenv.USER'
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