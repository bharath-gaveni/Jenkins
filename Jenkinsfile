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
            steps {
                script {
                    sh """
                    echo "Building"
                    echo role: ${ROLE}
                    sleep 11
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