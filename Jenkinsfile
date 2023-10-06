pipeline{
agent {node { label 'agent1'} }
environment{
    user = 'alekhya'
}
parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')

        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')

        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')

        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')

        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }

    
stages {

    stage ('parallel stage')
    {
        parallel{
            stage ('stage A')
            {
                steps {
                    echo 'on stage A'
                    sleep 10
                }
            }
            stage ('stage B')
            {
                steps{
                    echo 'on stage B'
                    sleep 10
                }
            }
            stage ('stage C'){
                stages{
                    stage ('stage D') {
                        steps {
                            echo 'stage D - sequential'
                            sleep 10
                        }
                    }
                    stage ('stage E') {
                        steps {
                            echo 'stage E - sequential'
                            sleep 10
                        }
                    }
                }
            }

        }
    }
    
    
    stage('input') {
            input {
                message "Should we continue?"
                ok "Yes, we should."
                parameters {
                    string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
                }
            }
            steps {
                echo "Hello, ${params.PERSON}, nice to meet you."
            }
        }

    stage ('parameters') {
        steps{
            echo "Hello ${params.PERSON}"
            echo "choice to select ${params.choices}"
            echo "boolean ${params.TOGGLE}"
        }
    }
    stage ('envexample1') {
        steps{
            echo "printenv - prints all environemnt variables. We can use them in program if needed"
            sh 'printenv' 
            sh 'echo "user name : $USER"'
        }
    }
    /* stage('Example') {
            environment { 
                AUTH = credentials ('ssh-auth') 
            }
            steps {
                sh 'printenv'
            }
        } */



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