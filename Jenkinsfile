pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/DevamSuryawanshi/jenkins-project.git'
            }
        }
        
        stage('Install Dependencies & Test') {
            steps {
                sh '''
                    python3 -m venv venv || python -m venv venv
                    . venv/bin/activate || venv\\Scripts\\activate
                    pip install --upgrade pip
                    if [ -f requirements.txt ]; then pip install -r requirements.txt; fi
                '''
            }
        }
    }
    
    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check stage logs for details.'
        }
    }
}
