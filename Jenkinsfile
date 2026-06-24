pipeline {
agent {
docker {
image 'node:22-alpine'
}
}

options {
    ansiColor('xterm')
}

stages {
    stage('Install Dependencies') {
        steps {
            sh 'node -v'
            sh 'npm -v'
            sh 'npm ci'
        }
    }

    stage('Build') {
        steps {
            sh 'npm run build'
        }
    }

    stage('Unit Tests') {
        steps {
            sh 'npm ls vitest'
            sh 'npm run test:unit'
        }
    }

    stage('Deploy') {
        agent {
            docker {
                image 'alpine'
            }
        }
        steps {
            echo 'Mock deployment was successful!'
        }
    }
}

post {
    always {
        echo 'Pipeline finished.'
    }
    success {
        echo 'Build and tests passed.'
    }
    failure {
        echo 'Build or tests failed.'
    }
}

}