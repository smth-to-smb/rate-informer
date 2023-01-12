pipeline {
  environment {
     QODANA_TOKEN= credentials('qodana-token')
     QODANA_REMOTE_URL="${GIT_URL}"
     QODANA_BRANCH="${GIT_BRANCH}"
     QODANA_REVISION="${GIT_COMMIT}"
     QODANA_CHECKOUT_DIR="${WORKSPACE}"
     
  }
     agent {
        docker {
            args '''
                -v "$QODANA_CHECKOUT_DIR" + :/data/project
                --entrypoint=""
            '''
            image 'jetbrains/qodana-php:2022.3-eap'
        }
    }

    stages {
        stage('Qodana') {
            steps {
                sh "echo $QODANA_REMOTE_URL"
                sh "echo $QODANA_CHECKOUT_DIR"
                sh "qodana --project-dir=/data/project"
            }
        }
    }
}
