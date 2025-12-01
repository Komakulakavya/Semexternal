pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'stage1 is Building...'
                echo "node name: ${env.NODE_NAME}"
                echo "workspace: ${env.WORKSPACE}"
                echo "artifact: ${env.BUILD_NUMBER}"
            }
        }

        stage('Test') {
            steps {
                echo 'stage2 is Testing...'
                echo "node name: ${env.NODE_NAME}"
                echo "workspace: ${env.WORKSPACE}"

                bat '''
                    findstr /C:"Contact form" index.html >nul
                    if %ERRORLEVEL%==0 (
                        echo Test Passed
                    ) else (
                        echo Test Failed
                        exit 1
                    )
                '''
            }
        }
    }

    post {
        success {
            echo 'The pipeline has succeeded!'
        }
        failure {     // <<<< use lowercase failure
            echo 'The pipeline has failed.'
        }
    }
}
