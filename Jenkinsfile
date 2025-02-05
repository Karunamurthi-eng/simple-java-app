pipeline {
    agent any
    stages {
        stage("init") {
            steps {
                script {
                    gv = load "script.groovy"
                }
            }
        }
        stage("build jar") {
            steps {
                script {
                    echo "building jar"
                    // gv.buildJar()
                }
            }
        }
        stage("build image") {
            steps {
                script {
                    echo "building image"
                    // gv.buildImage()
                }
            }
        }
        stage("deploy") {
            steps {
                script {
                    def dockerCmd = "docker run -p 3080:3080 -d karunadevops/my-repo:1.0"
                    sshagent(['ec2-server-key']) {
                        sh """
                            ssh -o StrictHostKeyChecking=no ec2-user@3.110.119.139 \\
                            "${dockerCmd}"
                        """
                    }
                    echo "deploying"
                    // gv.deployApp()
                }
            }
        }
    }
}
