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
}