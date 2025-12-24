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
                // Using your local rule file to catch the AWS Key
                sh 'semgrep scan --config=semgrep-rules.yaml --error .'
            }
        }

        stage('Deploy') {
            steps {
                echo '✅ Code is Safe. Deploying...'
                
                // DEBUG: This lists the permissions of the destination folder so we can see if Jenkins can access it
                sh 'ls -la /home/prangan/Downloads/prod-server/'
                
                // FORCE COPY: The '-f' flag forces the overwrite if the file exists
                sh 'cp -f index.html /home/prangan/Downloads/prod-server/index.html'
            }
        }
    }
}
