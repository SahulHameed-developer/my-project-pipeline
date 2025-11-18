pipeline{
    agent any
    // here any = keyword given by Jenkins
    // any = any available server where Jenkins can run the pipeline
    // right now the available server is the same EC2 server where Jenkins is installed
    // so any = current server

    tools{
        maven 'mymaven'
        // mymaven is the name given while configuring maven in Jenkins settings
        // here mymaven = version of maven installed on the Jenkins server
    }

    stages{
        stage('CLone the repo'){
            steps{
                // actual code to be executed
                // shell commands, calling other jobs, etc
                // git branch: 'main', url: ''
                git branch: 'master', url: 'https://github.com/SahulHameed-developer/my-project-pipeline.git'
                // sh 'mvn clean install'
            }
        }

        stage('Parallel Compile and Code Analysis'){
            parallel{
                stage('Compile the code'){
                    steps{
                        sh 'mvn compile'
                    }
                }

                stage('Code Analysis'){
                    steps{
                        sh 'mvn pmd:pmd'
                    }
                }
            }
        }

        // stage('Compile the code'){
        //     steps{
        //         sh 'mvn compile'
        //         // sh 'mvn pmd:pmd'
        //         // If using windows server, use bat 'mvn compile' instead of sh
        //     }
        // }

        // stage('Test the code'){
        //     steps{
        //         sh 'mvn test'
        //     }
        // }

        // stage('Code Analysis'){
        //     steps{
        //         sh 'mvn pmd:pmd'
        //     }
        // }

        // stage('Build the code'){
        //     steps{
        //         sh 'mvn package'
        //     }
        // }
    }
}