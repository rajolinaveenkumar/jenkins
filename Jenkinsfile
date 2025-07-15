pipeline {
    agent any

    environment {
        project = "expense"
        component = "jenkins"
        environment = "prod"
    }

    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }

    stages{

        stage('Build') {
            steps {
                script {
                    sh """
                        echo "Hello this is build"
                        echo "project: $project"
                        echo "Hello ${params.PERSON}"

                        echo "Biography: ${params.BIOGRAPHY}"

                        echo "Toggle: ${params.TOGGLE}"

                        echo "Choice: ${params.CHOICE}"

                        echo "Password: ${params.PASSWORD}"
                    """
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    sh """
                        echo "This is the test"
                        echo "componet: $component"
                    """
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    sh """
                        echo "this is deploy"
                        echo "environment: $environment"
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