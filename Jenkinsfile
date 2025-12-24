pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Security Gate') {
            steps {
                echo '🛡️ Scanning for Viruses...'
                // We use our LOCAL rule file (semgrep-rules.yaml)
                // This forces it to use the logic we just wrote
                sh 'semgrep scan --config=semgrep-rules.yaml --error .'
            }
        }

        stage('Deploy') {
            steps {
                echo '✅ Code is Safe. Deploying...'
                // Copy the website file to the "Production Server"
                sh 'cp index.html /home/prangan/Downloads/prod-server/index.html'
            }
        }
    }
}
