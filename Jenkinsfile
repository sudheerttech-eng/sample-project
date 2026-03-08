pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/sudheerttech-eng/sample-project'
            }
        }

        stage('Build') {
            steps {
                sh './hello.sh'
            }
        }
    }

    post {
        always {
            emailext(
                subject: "Jenkins Build - ${currentBuild.fullDisplayName}",
                body: """Build result: ${currentBuild.currentResult}
                Console log: ${env.BUILD_URL}console""",
                to: 'your-email@example.com'
            )
        }
    }
}

