pipeline {
    agent any 
    environment {
        NEW_VERSION = '1.3.0' //calculated or extracted
        //SERVER_CREDENTIALS = credentials('github-ayslan') GLOBAL
    }
    stages {
        stage("build") {
            steps {
                echo 'building the application...'
                echo "building version ${NEW_VERSION}"
            }
        }
        stage("test") {
            when {
                expression {
                    BRANCH_NAME == 'dev'  || BRANCH_NAME == 'main'
                }
            }
            steps {
                echo 'testing the application...'
            }
        }
        stage("deploy") {
            steps {
                echo 'deploying the application...'
                withCredentials([
                    usernamePassword(credentials: 'github-ayslan', usernameVarible: USER, passwordVariable: PWD)
                ]) {
                    echo "some script ${USER} ${PWD}"
                }
                //echo "deploying with ${SERVER_CREDENTIALS}"
            }
        }
    }
    // post { POST PIPELINE ACTIONS
    //     always {
    //         // 
    //     }
    //     success {
    //         // 
    //     }
    //     failure {
    //         // 
    //     }
    // }
}