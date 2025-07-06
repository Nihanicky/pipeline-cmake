pipeline {
    agent { label 'linuxgit' }
    
    environment {
        GIT_REPO = 'https://gitlab.com/sandeep160/pipeline-e2e.git'
        BRANCH = 'main'
    }
    
    stages {
        stage('Clean Workspace') {
            steps {
                echo 'CLeaning workspace'
                deleteDir()
            }
        }
        stage('Checkout') {
            steps {
                echo "Cloning the repo from Gitlab ........."
                git branch: "${BRANCH}",
                    url: "${GIT_REPO}",
                    credentialsId: 'gitlab-creds'
            }
        }
        stage('Build') {
            steps {
                sh 'dos2unix build.sh'
                sh 'chmod +x build.sh'
                sh 'bash build.sh'
            }
        }
    }
}
