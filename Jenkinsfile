pipeline {
    agent any

    environment {
        SSH_KEY_ID = 'jenkins-integration'
        DEPLOYMENT_SERVER = '65.2.169.153'
        DEPLOYMENT_PATH = '/home/ubuntu/website6'
        GIT_URL = 'git@github.com:NarayanaNunna/Jenkins_Sonarcube_Docker-Project.git'
        GIT_BRANCH = 'main'
    }

    stages {
        stage('Initializing') {
            steps {
                script {
                    // Accept the host key using ssh-keyscan
                    sh "ssh-keyscan -H ${DEPLOYMENT_SERVER} >> ~/.ssh/known_hosts"

                    // Use the configured SSH key from Jenkins credentials
                    sshagent(['jenkins-integration']) {
                        sh "ssh ubuntu@${DEPLOYMENT_SERVER} 'git clone ${GIT_URL} -b ${GIT_BRANCH} ${DEPLOYMENT_PATH}'"
                    }
                }
            }
        }
    }
}
