pipeline {
    agent any 
    tools {
        maven,
        gradle,
        jdk
    }
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
                script {
                    withCredentials([
                        usernamePassword(credentialsId: 'github-ayslan', usernameVariable: GIT_USER, passwordVariable: GIT_PWD)
                    ]) {
                        
                    }
                }
                echo "some script ${env.GIT_USER} ${env.GIT_PWD}"
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