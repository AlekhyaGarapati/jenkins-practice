pipeline{
agent {node {label:agent1}}
stages {
    stage ('build'){
        steps{
            echo "build"
        }
    }
    stage ('scan') {
        steps{
            echo "scan"
        }
    }
    stage ("deploy"){
        step {
            echo "deploy"
        }
    }
}
}