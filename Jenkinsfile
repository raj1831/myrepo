pipeline{
    agent any
    
    stages{
        stage("SCM Checkout"){
            steps{
                git credentialsId: '4b651eed-7598-4ce6-ad70-2d18f8ca2e47', url: 'https://github.com/raj1831/myrepo.git'
            }
            post{
                always{
                    echo "========always========"
                }
                success{
                    echo "========A executed successfully========"
                }
                failure{
                    echo "========A execution failed========"
                }
            }
        }
    
    stage("uploading to ec2"){
            steps{
                sshagent(['a401068a-e154-463d-b8b3-5aca1b9422e4']) {
                    sh """
                    scp -o StrictHostKeyChecking=no index.html ec2-user@3.144.131.162:/var/www/html
                    """
                }
            }
            post{
                always{
                    echo "========always========"
                }
                success{
                    echo "========A executed successfully========"
                }
                failure{
                    echo "========A execution failed========"
                }
            }
        }

    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}
