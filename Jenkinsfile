pipeline {
     agent{
            docker{
                image 'node:18-alpine'
                reuseNode true
            }
        }
    stages {
        stage('Build') {
            steps {
                cleanWs()
                sh '''
                ls -la
                node --version
                npm --version
                npm ci
                ls -la
                npm run build
                ls -la
                '''
            }
        }
        stage('Test'){
            steps{
                sh '''
                test -f build/index.html
                npm test
                ls -la
                '''
            }
        }
    }
}
