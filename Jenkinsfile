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
        stage('first stage') {
            steps {
                echo "jenkins first stage"
            }
        }
        //second stage
        stage('second stage') {
            steps {
                echo "jenkins second stage"
            }
        }
        //third stage
        stage('third stage') {
            steps {
                echo "jenkins third stage"
            }
        }
    }

}