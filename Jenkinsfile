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
                        def out = powershell(returnStdout: true, script: '$(pwd).Path')
                        println out
                    }
                }
            }
        }
    }
}
