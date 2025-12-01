stage('Test') {
    steps {
        echo 'stage2 is Testing...'
        echo "node name: ${env.NODE_NAME}"
        echo "workspace: ${env.WORKSPACE}"

        bat '''
            set FILE=index.html
            set PASS=true
            rem Checking required fields
            findstr /C:"Contact form" %FILE% >nul || set PASS=false
            findstr /C:"name" %FILE% >nul || set PASS=false
            findstr /C:"email" %FILE% >nul || set PASS=false
            findstr /C:"subject" %FILE% >nul || set PASS=false
            findstr /C:"message" %FILE% >nul || set PASS=false

            if "!PASS!"=="true" (
                echo All required fields are present.
            ) else (
                echo One or more fields are missing.
                exit 1
            )
        '''
    }
}

