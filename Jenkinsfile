pipeline 
{
    agent none
    stages 
    {
        stage('Say Hello') 
        {
            steps 
            {
                powershell (returnStdout: true, script: 'docker run --rm -d -t msbuild15testplatform')
            }
        }
    }
}
