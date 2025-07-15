pipeline {
    agent any

    stages{

        stage('Build') {
            steps {
                script {
                    sh """
                        echo "Hello this is build"
                    """
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    sh """
                        echo "This is the test"
                    """
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    sh """
                        echo ""
                    """
                }
            }
        }
    }

    post {
        always {
            echo "this will run always"
        }
        success {
            echo "this run only at success"
        }
        failure {
            echo "this runs only at failure"
        }
        unstable {
            echo "tests fail or quality issues"
        }
        aborted {
            echo "Build was manually stopped"
        }
        changed {
            echo "Build result chnaged from last time"
        }
        fixed {
            echo "it was broken, now it's fixed"
        }
        regression {
            echo "it was working, now it's broken"
        }
        unsuccessful {
            echo "something went wrong"
        }
        cleanup {
            echo "Final cleanup always last"
        }
    }
}