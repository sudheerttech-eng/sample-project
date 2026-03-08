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
	        sh 'chmod +x hello.sh'
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
                to: 'sudheert.tech@gmail.com'
            )
        }
    }
}

