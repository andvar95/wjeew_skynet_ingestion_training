@Library("workflowlibs@master") _

pipeline {
    agent { label 'spark' }

    parameters {
            string(name: "UUAA", description: "UUAA corresponding the namespace to execute the job.", defaultValue: "")
            choice(name: "JobGroup", description: "Job group.", choices: "processing\nproduction\nsandbox\negression" )
            string(name: "JobName", description: "Job name to execute.", defaultValue: "")
            string(name: "Params", description: "Semicolon-separated params to send to this job execution.", defaultValue: "")
            choice(name: "Sync", description: "Executes the job and waits until it finishes.", choices: "true\nfalse")
        }

    environment {
        skynet_dataproc_endpoint = "https://daas-hd2.work.mx.ether.igrupobbva"
    }

    stages {
        stage('Checkout Global Library') {
            steps {
                script{
                    globalBootstrap {
                        libraryName   = "datio-workflowlibs"
                        libraryBranch = "skynet"
                        entrypointParams = [
                            nodeLabel         : "spark",
                            projectType       : "SKYNET"
                        ]
                    }
                }
            }
        }
    }

    post {
        always {
            echo "We have been through the entire pipeline"
        }
        changed {
            echo "There have been some changes from the last build"
        }
        success {
            echo "Build successful"
        }
        failure {
            echo "There have been some errors"
        }
        unstable {
            echo "Unstable"
        }
        aborted {
            echo "Aborted"
        }
    }
}
