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
                    node
                    {
                        powershell(script: '$(pwd).Path')
                    }
                }
            }
        }
    }
}
