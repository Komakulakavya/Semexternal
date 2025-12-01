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
                    set FILE=index.html

                    echo Checking form fields...

                    findstr /C:"<h1>Contact form</h1>" %FILE% >nul || (echo Missing heading & exit 1)
                    findstr /C:"placeholder=\\"name\\"" %FILE% >nul || (echo Missing Name field & exit 1)
                    findstr /C:"placeholder=\\"email\\"" %FILE% >nul || (echo Missing Email field & exit 1)
                    findstr /C:"placeholder=\\"subject\\"" %FILE% >nul || (echo Missing Subject field & exit 1)
                    findstr /C:"placeholder=\\"message\\"" %FILE% >nul || (echo Missing Message field & exit 1)
                    echo All fields found - Test Passed!
                '''
            }
        }
    }

    post {
        success {
            echo 'The pipeline has succeeded!'
        }
        failure {
            echo 'The pipeline has failed.'
        }
    }
}

