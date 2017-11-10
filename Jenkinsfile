pipeline 
{
    agent none
    stages 
    {
        stage('Say Hello') 
        {
            steps 
            {
                script
                {
                    powershell(script: '$(pwd).Path')
                }
            }
        }
    }
}
