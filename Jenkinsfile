pipeline
{
    agent any

    stages
    {
        stage('Build')
        {
            steps
            {
                echo 'stage1 is Building...'
                echo "node name: ${env.NODE_NAME}"
                echo "workspace: ${env.WORKSPACE}"
                echo "artifact: ${env.BUILD_NUMBER}"
            }
        }
        stage('Test')
        {
            steps
            {
                echo 'stage2 isTesting...'
                echo "node name: ${env.NODE_NAME}"
                echo "workspace: ${env.WORKSPACE}"  
                grep -q "Contact form" index.html && echo "Test Passed" || (echo "Test Failed"; exit 1)
            }
        }
    }
    post
    {
        success
        {
            echo 'The pipeline has succeeded!'
        }
        Failure
        {
            echo 'The pipeline has failed.'
        }
    }
}
        