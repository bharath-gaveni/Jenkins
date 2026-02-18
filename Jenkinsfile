// pipeline {
//     agent any
//     stages {
//         stage('Example') {
//             steps {
//                 echo 'Hello World'
//             }
//         }
//     }
// }



// pipeline {

//     agent {
//         node {
//             label 'AGENT-1'
//         }
//     }

//     stages {
//         //first stage
//         stage('Build') {
//             steps {
//                 echo "Building"
//             }
//         }
//         //second stage
//         stage('Test') {
//             steps {
//                 echo "Testing"
//             }
//         }
//         //third stage
//         stage('Deploy') {
//             steps {
//                 echo "Deploying"
//             }
//         }
//     }
//         post {
//             always {
//                echo 'I will run irrespective of if pipeline is success or failure'
//                cleanWs()
//             }
//             success {
//                 echo 'success'
//             }

//             failure {
//                 echo 'failure'
//             }
//         }
// }

// using script

pipeline {

    agent {
        node {
            label 'AGENT-1'
        }
    }

    environment {
        ROLE = "AWS DevSecOps Engineer"
    }

    options {
        timeout(time: 10, unit: 'SECONDS')
        disableConcurrentBuilds()
    }

    //parameters testing for webhook
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')

        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')

        booleanParam(name: 'DEPLOY', defaultValue: false, description: 'Toggle this value')

        choice(name: 'CHOICE', choices: ['FIVE', 'Two', 'Three'], description: 'Pick something')

        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }

    stages {
        //first stage
        stage('Build') {
            steps {
                script {
                    sh """
                    echo "Building"
                    echo role: ${ROLE}
                    env
                    """
                }
            }
        }
        //second stage
        stage('Test') {
             steps {
                script {
                    sh """
                    echo "Testing"
                    echo role: ${ROLE}
                    """
                }
            }
        }
        //third stage
        stage('Deploy') {
                 when {
                    expression { "$params.DEPLOY" == "true"}
            }
                     input {
                    message "Should we continue?"
                    ok "Yes, we should."
                    submitter "alice,bob"
                    parameters {
                        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
                    }
                        }
            steps {
                script {
                    sh """
                    echo "Building"
                    echo role: ${ROLE}
                     echo "Hello ${params.PERSON}"

                    echo "Biography: ${params.BIOGRAPHY}"

                    echo "Toggle: ${params.TOGGLE}"

                    echo "Choice: ${params.CHOICE}"

                    echo "Password: ${params.PASSWORD}"

                    sleep 10
                    """
                }
            }
        }
    }
        post {
            always {
               echo 'I will run irrespective of if pipeline is success or failure'
               cleanWs()
            }
            success {
                echo 'success'
            }

            failure {
                echo 'failure'
            }
            aborted {
                echo 'pipeline is taking time then expected please check'
            }
        }
}