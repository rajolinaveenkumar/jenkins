pipeline {
    agent {
        label 'agent-1-label'
    }

    environment {
        project = "expense"
        component = "jenkins"
        
        DEPLOY_TO = "prod"  
        env = "prod" 
        env_name = "non-prod"      
        
    }

    options {
        timeout(time: 20, unit: 'MINUTES')             
        disableConcurrentBuilds()                   
        disableResume()                                
        preserveStashes(buildCount: 5)                 
        quietPeriod(30)                                                   
        timestamps()                                   
        ansiColor('xterm')                             
        parallelsAlwaysFailFast()                      
    }
    
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Naveen Rajoli', description: 'Who should I say hello to?')
        text(name: 'DEPLOY_TEXT', defaultValue: 'One\nTwo\nThree\n', description: '')
        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
        choice(name: 'environment_name', choices: ['dev', 'staging', 'prod'], description: 'Pick something')
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
            // input {
            //     message "should we continue?"
            //     ok "yes please proceed"
            //     parameters {
            //         string(name: 'PERSON', defaultValue: 'Mr Naveen Rajoli', description: 'Who should I say hello to?')
            //     }
            // }
            steps {
                script {
                    sh """
                        echo "This is the test" 
                        echo "componet: $component"
                    """
                }
            }
        }

        stage('Environmet') {
            when {
                // environment name: 'DEPLOY_TO', value: 'prod'
                environment name: 'environment_name', value: 'prod'
                
            }
            steps {
                script {
                    sh """
                        echo "this is deploy"
                        echo "environment: $env (note: env wont work bcz its shell varaible)" 
                        echo "environment: $env_name"
                        
                    """
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    sh """
                        echo "this is deploy"
                        echo "environment: $DEPLOY_TO"
                        
                    """
                }
            }
        }

        stage('parallel Stage') {
            parallel {
                stage('stage-1') {
                    steps {
                        script {
                            sh """ 
                                echo "this is parallel stage-1"
                            """
                        }
                    }
                }
                stage('stage-2') {
                    steps {
                        script {
                            sh """
                                echo "this is parallel stage-1"
                            """
                        }
                    }
                }
            }
        }
    }

    post {
        always {
            echo "this will run always"
            deleteDir()
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