pipeline 
{
    agent none
    stages 
    {
        stage('Say Hello') 
        {
            steps 
            {
                powershell ('docker run --rm -d -t msbuild15testplatform')
            }
        }
    }
}
