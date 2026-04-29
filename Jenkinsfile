pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo "Creating build output file"
                sh '''
                  mkdir output
                  echo "Hello from Jenkins Artifact Demo" > output/app.txt
                  date >> output/app.txt
                '''
            }
        }
    }

    post {
        success {
            echo "Archiving artifacts"
            archiveArtifacts artifacts: 'output/*.txt'
        }
        always {
            echo "Cleaning workspace"
            cleanWs()
        }
    }
}
