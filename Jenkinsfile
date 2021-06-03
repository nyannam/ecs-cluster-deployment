pipeline {
    agent none
    options {
        buildDiscarder(logRotator(numToKeepStr: '10'))
        disableConcurrentBuilds()
        timestamps()
        ansiColor('xterm')
    }
    stages {

        stage('Deploy| Development') {
            agent {
                label 'Development'
            }
            environment {
                PATH=".:$PATH"
                ARCH_PATH="cloudformation/arch-yamls/cfn-ecs.yml"
                VAR_PATH="cloudformation/var-files/devl.json"
                STACK_NAME="ecs-cluster"
                S3_BUCKET="devlbucket-system"
                S3_PATH="templates/ecs.yml"
            }
            steps {
                sh """
                  
                """
            }
            when { not { changeRequest() } }
        }
        stage('Deploy| Production') {
            agent {
                label 'Production'
            }
            environment {
                PATH = ".:$PATH"
                ARCH_PATH = "cloudformation/arch-yamls/cfn-ecs.yml"
                VAR_PATH = "cloudformation/var-files/prod.json"
                STACK_NAME = "ecs-cluster"
                S3_BUCKET= "prodbucket-system"
                S3_PATH = "templates/ecs.yml"
            }
            steps {
                sh """
                
                """
            }
            when {
                branch 'master'
                not {
                    changeRequest()
                }
            }
        }
    }
}