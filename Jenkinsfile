pipeline {
    agent { 
        node {
            label 'docker-agent-alpine'
        }
    }
    triggers {
        pollSCM '5 * * * *'
    }
    stages {
        stage('Install HTMLTidy') {
            steps {
                sh 'apk add --no-cache tidyhtml'
            }
        }
        stage('HTML Validation') {
            steps {
                sh '''
                tidy -q -e index.html
                '''
            }
        }
    }
    post {
        failure {
            echo 'Pipeline failed. Take necessary actions...'
            // You can add more post-failure actions here
        }
        success {
            echo 'Pipeline succeeded. Perform success actions...'
            // You can add more post-success actions here
        }
    }
}
