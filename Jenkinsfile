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



pipeline {

    agent {
        node {
            label 'AGENT-1'
        }
    }

    stages {
        //first stage
        stage('Build') {
            steps {
                echo "Building"
            }
        }
        //second stage
        stage('Test') {
            steps {
                echo "Testing"
            }
        }
        //third stage
        stage('Deploy') {
            steps {
                echo "Deploying"
            }
        }
    }
        post {
            always {
                'I will run irrespective of if pipeline is success or failure'
            }
        }
}