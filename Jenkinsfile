pipeline{
agent {node { label 'agent1'} }
stages {
    stage ('build'){
        steps{
            echo "build from webhook"
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