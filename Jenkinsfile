pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                script {
                    // Compile the .cpp file
                    sh '''
                        g++ -o sample sample.cpp
                    '''
                    build job: 'PES2UG21CS14000-1'
                }
            }
        }
        
        stage('Test') {
            steps {
                script {
                    // Execute the compiled .cpp file
                    sh './sample'
                }
            }
        }
        
        stage('Deploy') {
            steps {
                // Add deployment steps here if needed
                echo 'Deployed successfully'
            }
        }
    }
    
    post {
        always {
            script {
                // Display "pipeline failed" in case of any errors within the pipeline
                currentBuild.result = currentBuild.result ?: 'SUCCESS'
                if (currentBuild.result == 'FAILURE') {
                    echo 'pipeline failed'
                }
            }
        }
    }
}
